---
title: "Optimization by PYOMO in Python: A complete working example"
date: 2022-07-15
draft: false
image: post-image.png
aliases: ["/optimization-with-pyomo-cwe/"]
---
### Step 1. Defining the optimization model

The optimization model can be defined by a Python function. The inputs to this function would be the sets, parameters, and variables. The output would be the symbolic objective(s) and constraints.

For instance, the following optimization model maximizes the net present value of executing improvement projects on some facilities. Selecting project _i_ for facility _j_ is denoted by binary variable _x_, and determining the budget for these improvements is represented by positive variable _y_. The parameters _c_ and _a_ denote the net present value and investment required for each project for each facility, respectively. The total budget for the headquarter to implement these improvement projects is indicated by the parameter*b*. Finally, the sets _J_ and _I_ represent the number of facilities and projects, respectively. Considering that the total amount of investment for all facilities should be lower than the entire budget available, to maximize the total net present value, the optimization model can be created as follows:

```python
import itertools as it

def model(I,J,x,y):
    objs = {0: sum(c[j,i]*x[j,i] for j,i in it.product(J,I))}
    cons = {0: {j: sum(a[j,i]*x[j,i] for i in I) <= y[j] for j in J},
            1: {0: sum(y[j] for j in J) <= b}}
    return objs, cons
```

Notably, this part is independent of any optimization interface used. Also, since I am using `itertools` module for constraints or summations with multiple indices, we need to import it.

### Step 2. Using the optimization interface

In this next step, we configure the optimization interface used to generate a solver-friendly intermediary file (e.g., .mps or .lp). Usually, the most critical setting in this step is to create sets and variables and feed them to the model previously created. Again, I use a Python function to adjust the interface:

```python
import pyomo.environ as op

def interface():

    #Used for creating the environment and naming it in Pyomo
    m = op.ConcreteModel(name)

   #Used for defining sets in PYOMO
    m.I = op.Set(initialize=I)
    m.J = op.Set(initialize=J)

    #Used for defining variables in PYOMO
    m.x = op.Var(m.J,m.I, domain=op.Binary)
    m.y = op.Var(m.J, domain=op.PositiveReals)

    #Used for feeding created sets and variables to the model (general)
    objs, cons = model(m.I,m.J,m.x,m.y)

    #Used for defining objective(s) in PYOMO
    m.OBJ = op.Objective(expr=objs[0],sense=op.maximize)

    #Used for defining constraints in PYOMO
    m.constraint = op.ConstraintList()
    for keys1 in cons:
        for keys2 in cons[keys1]: m.constraint.add(expr=cons[keys1][keys2])

    return m
```

### Step 3. Adjusting the solver

In this next step, we feed the interface-generated file to a solver. Since no solver comes with PYOMO pre-installed, I use online solvers from the NEOS Server. For instance, as the proposed model is MILP, I use CPLEX to solve it. Moreover, I consider three inputs for a solver, `showmodel`, `solvemodel`, and `showresult`. If each set to true, the corresponding task would be implemented. Showing the model is suitable in the validation stage. But, we usually do not need it during sensitivity analysis. Solving the model is always required unless we make our optimization model with try and error and want to check its overall look and feel. Finally, showing the result is helpful for validation or sensitivity analysis.

```python
import os

def solve(showmodel=True,solvemodel =True,showresult =True):

    #Used for creating the solver-friendly files
    m = interface()

    #Used for validating the model
    if showmodel: print("Model:",m)

    #Used for calling solvers in PYOMO
    if solvemodel:
        os.environ['NEOS_EMAIL'] = 'username@email.com'
        solver_manager = op.SolverManagerFactory('neos')
        results = solver_manager.solve(m, solver = "cplex")

    #Used for validating the model
    if showresult:
        print(results)
        op.display(m)

    return m
```

### Step 4. Defining or feeding datasets

In this next step, we need data. It is common to create data randomly to stress test a model. However, one should pay attention to the consequences. The consequences can be WRONG infeasibility alerts, numerical INSTABILITY in the solving process, etc. It is better to understand your data and the relationship between its elements. For instance, if you are randomly creating demand values, the capacity of your facilities should not be lower. Overall, some parameter tuning is required EVEN IF you are testing your model on arbitrarily generated datasets. If the datasets are from real-world applications, parameter tuning is STILL needed. For instance, try not to feed your model with VERY LARGE or SMALL values. The data for the optimization model introduced in step 1 is generated as follows:

```python
import numpy as np

#Used for reproducibility of the results:
np.random.seed(10)

#Name of the model:
name = "Facilities Investment Planning"

#Cost of implementing each project for each facility
a = np.random.uniform(10, 20, (5, 6))

# Net present value (benefit) of implementing each project for each
c = np.random.uniform(100, 300, (5, 6))

#Total budget available
b = 80

#Set of facilities
J = range(a.shape[0])

#Set of improvement projects
I = range(a.shape[1])
```

### Step 5. Implementing the model

In this next step, we need to implement the model to see if it generates feasible, logical, and optimal solutions.

```python
#Implementation after feeding data
m = solve(showmodel=True,solvemodel =True,showresult =True)
```

### Step 6. Visualizing the results

Understanding the obtained results is easy for one who has developed the model. However, what if these results will be presented to an audience without involvement in the process? In this step, one should try to find the BEST plots and figures to visualize the data. In some cases, generating a TABLE is even enough. For this simple optimization problem, I visualize the binary variable _x_ using `imshow` from `matplotlib.pyplot` module in Python and a simple bar chart to show the investment amount for each facility. I also can visualize the parameters to see if the relationship between the inputs and outputs of a model is valid and logical.

```python
import matplotlib.pyplot as plt

plt.figure(1)
x = np.zeros(shape=(5, 6))
for j in J:
    for i in I:
        if m.x.get_values()[(j,i)]==1: x[j,i]=1
plt.title("Investment Portfolio")
plt.xlabel("Projects")
plt.ylabel("Facilities")
plt.imshow(x)
plt.colorbar()

plt.figure(2)
plt.title("Investment Amount")
plt.xlabel("Facilities")
plt.ylabel("Amount of investment")
plt.bar(list(m.y.get_values().keys()),list(m.y.get_values().values()))

plt.figure(3)
plt.title("Cost")
plt.xlabel("Projects")
plt.ylabel("Facilities")
plt.imshow(a)
plt.colorbar()

plt.figure(4)
plt.title("Benefit")
plt.xlabel("Projects")
plt.ylabel("Facilities")
plt.imshow(c)
plt.colorbar()
```

### Step 7. Sensitivity analysis

After validating the model, we need robustness checking. That means, how are the results robust to changes? What is the trend in changes of outputs while inputs are changed? This step is the most important as it introduces the model's behavior for other cases. It is also a simple method to see the effect of uncertainties in the values of the parameters. It even empowers the whole neural networks we see in machine learning! Why? The changes in input parameters (e.g., number of layers or number of neurons in each layer) can affect accuracy (the objective). So it can help one determine the best structure for a neural network for the training dataset, to then be applied to the test dataset! A simple sensitivity analysis is to increase or decrease the values of parameters one-by-one to see their effect on the objective (response), as follows:

```python
S = range(5)
aa = a.copy()
for s in S:
    a = a*(1+s/len(S))
    m = solve(showmodel=False,solvemodel=True,showresult=False)
    print(op.value(m.OBJ))
a = aa

bb = b.copy()
S = range(5)
for s in S:
    b = b*(1-s/len(S))
    m = solve(showmodel=False,solvemodel=True,showresult=False)
    print(op.value(m.OBJ))
b = bb

cc = c.copy()
S = range(5)
for s in S:
    c = c*(1-s/len(S))
    m = solve(showmodel=False,solvemodel=True,showresult=False)
    print(op.value(m.OBJ))
c = cc
```

### The optimization pipeline

Based on the discussed steps, a generic optimization pipeline is as follows:

1. Defining the optimization model
2. Using the optimization interface
3. Adjusting the solver
4. Defining or feeding datasets
5. Implementing the model
6. Visualizing the results
7. Sensitivity analysis

### Conclusion

In this article, I proposed a working example for optimization with PYOMO in Python. Then, introduced an optimization pipeline that is generic and can be applied when an operations research scientist is modeling, solving, and analyzing an optimization problem. If the content was helpful, consider supporting the project FELOOP or sharing the content with your colleagues and friends! Also, feel free to contact me if there are any questions.
