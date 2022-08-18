---
title: "List of optimization packages in Python: Update 2022"
layout: post
description: Getting to know optimization packages in Python.
categories:
  - General
tags:
  - Optimization Programming Language
  - Python
author:
  - Keivan Tafakkori
image: "/images/interface-solvers.png"
comments: true
---

{% include update.html %}

{% include important.html content="If you know a specific package, which is missing, you may either contact me or comment here." %}

{% include warning.html content="The current list may have errors. If you found some, you may either contact me or comment here." %}

# Introduction

This article can be a comprehensive reference for academics and experts in industrial engineering (IE), supply chain management (SCM), operations research (OR), computer science (CS), machine learning (ML), simulation (SM), data science (DS), and others to get familiar with what is available for optimization in Python.

<div class="dark-bg">
    <video width="100%" height="600" autoplay loop muted class="no-margin">
        <source src="/images/interface-solver.mp4"></source>
    </video>
</div>

# Guide

| Package capability | Description                         |
| ------------------ | ----------------------------------- |
| `MINLP`            | Mixed integer nonlinear programming |
| `MIQP`             | Mixed integer quadratic programming |
| `MILP`             | Mixed integer linear programming    |
| `NLP`              | Nonlinear programming               |
| `IP`               | Integer programming                 |
| `LP`               | Linear programming                  |
| `CP`               | Constraint programming              |
| `GPP`              | General purpose programming         |

# MINLP+MIQP+MILP+NLP+IP+LP Packages

| Package         | Link                                                                  |
| --------------- | --------------------------------------------------------------------- |
| `casadi`        | [Official](https://web.casadi.org/)                                   |
| `gekko`         | [Official](https://machinelearning.byu.edu/)                          |
| `knitro`        | [Official](https://www.artelys.com/docs/knitro/index.html)            |
| `lindo`         | [Official](https://www.lindo.com/)                                    |
| `midaco`        | [Official](http://www.midaco-solver.com/index.php/download/python)    |
| `naginterfaces` | [Official](https://www.nag.com/)                                      |
| `octeract`      | [Official](https://octeract.gg/)                                      |
| `optalg`        | [Official](https://github.com/ttinoco/OPTALG)                         |
| `optmod`        | [Official](https://github.com/ttinoco/OPTMOD)                         |
| `pydrake`       | [Official](https://drake.mit.edu/)                                    |
| `pyomo`         | [Official](http://www.pyomo.org/)                                     |
| `pyscipopt`     | [Official](https://scipopt.org/)                                      |
| `xpress`        | [Official](https://www.fico.com/en/products/fico-xpress-optimization) |

# MIQP+MILP+IP+LP Packages

| Package       | Link                                                               |
| ------------- | ------------------------------------------------------------------ |
| `copt`        | [Official](https://www.shanshu.ai/copt)                            |
| `cplex`       | [Official](https://www.ibm.com/analytics/cplex-optimizer)          |
| `docplex`     | [Official](https://ibmdecisionoptimization.github.io/docplex-doc/) |
| `gurobipy`    | [Official](https://www.gurobi.com/)                                |
| `highs`       | [Official](https://highs.dev/)                                     |
| `localsolver` | [Official](https://www.localsolver.com/)                           |
| `mosek`       | [Official](https://docs.mosek.com/latest/pythonapi/index.html)     |
| `optlang`     | [Official](https://optlang.readthedocs.io/en/latest/)              |
| `sasoptpy`    | [Official](https://github.com/sassoftware/sasoptpy)                |

# MILP+IP+LP Packages

| Package      | Link                                                                |
| ------------ | ------------------------------------------------------------------- |
| `cvxopt`     | [Official](https://cvxopt.org/)                                     |
| `cvxpy`      | [Official](https://www.cvxpy.org/)                                  |
| `cylp`       | [Official](http://coin-or.github.io/CyLP/)                          |
| `flowty`     | [Official](https://flowty.ai/)                                      |
| `lpsolve55 ` | [Official](http://web.mit.edu/lpsolve/doc/Python.htm)               |
| `mindoptpy`  | [Official](https://solver.damo.alibaba-inc.com/doc/html/index.html) |
| `mip`        | [Official](https://www.python-mip.com/)                             |
| `ortools`    | [Official](https://developers.google.com/optimization)              |
| `picos`      | [Official](https://picos-api.gitlab.io/picos/)                      |
| `pulp`       | [Official](https://projects.coin-or.org/PuLP)                       |
| `pymprog`    | [Official](http://pymprog.sourceforge.net/)                         |
| `swiglpk`    | [Official](https://github.com/biosustain/swiglpk)                   |

# NLP+LP Packages

| Package       | Link                                                      |
| ------------- | --------------------------------------------------------- |
| `acadopy`     | [Official](https://github.com/force-h2020/acadopy)        |
| `acados`      | [Official](https://docs.acados.org/index.html)            |
| `cyipopt`     | [Official](https://pypi.org/project/ipopt/)               |
| `dymos`       | [Official](https://openmdao.github.io/dymos/)             |
| `gpkit`       | [Official](https://gpkit.readthedocs.io/en/latest/)       |
| `iminuit`     | [Official](https://pypi.org/project/iminuit/)             |
| `nlopt`       | [Official](https://nlopt.readthedocs.io/en/latest/)       |
| `nlpy`        | [Official](http://nlpy.sourceforge.net/)                  |
| `openmdao`    | [Official](https://openmdao.org/)                         |
| `openopt`     | [Official](http://openopt.org/)                           |
| `polyopt`     | [Official](https://github.com/PavelTrutman/polyopt)       |
| `pyipopt`     | [Official](https://github.com/xuy/pyipopt)                |
| `pyopt`       | [Official](http://www.pyopt.org/)                         |
| `scipy`       | [Official](https://scipy.org/)                            |
| `trustregion` | [Official](https://github.com/lindonroberts/trust-region) |
| `worhp`       | [Official](https://worhp.de/)                             |

# CP Packages

| Package         | Link                                                                                          |
| --------------- | --------------------------------------------------------------------------------------------- |
| `cplex`         | [Official](https://www.ibm.com/analytics/cplex-cp-optimizer)                                  |
| `cpmpy`         | [Official](https://github.com/CPMpy/cpmpy)                                                    |
| `gecode-python` | [Official](https://launchpad.net/gecode-python)                                               |
| `kalis`         | [Official](https://www.artelys.com/docs/kalis/index.html)                                     |
| `minizinc`      | [Official](https://minizinc-python.readthedocs.io/en/latest/index.html)                       |
| `optapy`        | [Official](https://www.optapy.org/docs/latest/planner-introduction/planner-introduction.html) |
| `ortools`       | [Official](https://developers.google.com/optimization/cp)                                     |
| `z3-solver`     | [Official](https://github.com/Z3Prover/z3)                                                    |

# GPP Packages

| Package                    | Link                                                                                  |
| -------------------------- | ------------------------------------------------------------------------------------- |
| `arm-mango`                | [Official](https://github.com/ARM-software/mango)                                     |
| `ax`                       | [Official](https://github.com/facebook/Ax)                                            |
| `bayesian-optimization`    | [Official](https://github.com/fmfn/BayesianOptimization)                              |
| `bayesianevolution`        | [Official](https://github.com/subhodipbiswas/BayesianEvolution)                       |
| `bayeso`                   | [Official](https://bayeso.readthedocs.io/en/main/)                                    |
| `bayesopt`                 | [Official](https://bayesopt.github.io/)                                               |
| `black-box`                | [Official](https://github.com/paulknysh/blackbox)                                     |
| `bolib`                    | [Official](https://gitlab.com/ibaidev/bolib)                                          |
| `cma`                      | [Official](https://github.com/CMA-ES/pycma)                                           |
| `cmaes`                    | [Official](https://github.com/CyberAgentAILab/cmaes)                                  |
| `cobyqa`                   | [Github](https://github.com/ragonneau/cobyqa)                                         |
| `cuopt`                    | [Official](https://developer.nvidia.com/cuopt-logistics-optimization)                 |
| `deap`                     | [Official](https://github.com/7ossam81/EvoloPy)                                       |
| `dfoalgos`                 | [Official](https://pypi.org/project/dfoalgos/)                                        |
| `dfogn`                    | [Official](https://pypi.org/project/DFOGN/)                                           |
| `dlib`                     | [Official](http://dlib.net/)                                                          |
| `evolopy`                  | [Official](https://github.com/7ossam81/EvoloPy)                                       |
| `evoopt`                   | [Official](https://github.com/tsyet12/EvoOpt)                                         |
| `freelunch`                | [Official](https://pypi.org/project/freelunch/)                                       |
| `gaft`                     | [Official](https://github.com/PytLab/gaft)                                            |
| `geneticalgorithm`         | [Official](https://github.com/rmsolgi/geneticalgorithm)                               |
| `goptpy`                   | [Github](https://github.com/redb0/gotpy)                                              |
| `gradient-free-optimizers` | [Github](https://github.com/SimonBlanke/Gradient-Free-Optimizers)                     |
| `gyopt`                    | [Official](http://sheffieldml.github.io/GPyOpt/)                                      |
| `hebo`                     | [Official](https://pypi.org/project/HEBO/)                                            |
| `heuristic_optimization`   | [Official](https://github.com/tjanson/heuristic_optimization)                         |
| `hpbandster`               | [Official](https://github.com/automl/HpBandSter)                                      |
| `hyperopt`                 | [Official](http://hyperopt.github.io/hyperopt/)                                       |
| `inspyred`                 | [Official](https://github.com/aarongarrett/inspyred)                                  |
| `mealpy`                   | [Official](https://github.com/thieu1995/mealpy)                                       |
| `mipego`                   | [Official](https://github.com/wangronin/MIP-EGO)                                      |
| `mystic`                   | [Official](https://github.com/uqfoundation/mystic)                                    |
| `nevergrad`                | [Official](https://facebookresearch.github.io/nevergrad/)                             |
| `niapy`                    | [Official](https://github.com/NiaOrg/NiaPy)                                           |
| `oasis`                    | [Official](https://github.com/MAfarrag/Oasis)                                         |
| `optuna`                   | [Official](https://optuna.org/)                                                       |
| `optuner`                  | [Official](https://opentuner.org/)                                                    |
| `opytimizer`               | [Official](https://github.com/gugarosa/opytimizer)                                    |
| `pagmo`                    | [Official](https://esa.github.io/pagmo2/index.html)                                   |
| `pdfo`                     | [Official](https://www.pdfo.net/index.html)                                           |
| `platypus`                 | [Official](https://platypus.readthedocs.io/en/latest/)                                |
| `proxmin`                  | [Official](https://github.com/pmelchior/proxmin)                                      |
| `psopt`                    | [Official](https://pypi.org/project/psopt/)                                           |
| `psopy`                    | [Official](https://github.com/jerrytheo/psopy)                                        |
| `py-bobyqa`                | [Official](https://numericalalgorithmsgroup.github.io/pybobyqa/build/html/index.html) |
| `pydogs`                   | [Official](https://pypi.org/project/pydogs/)                                          |
| `pygmo`                    | [Official](https://esa.github.io/pygmo2/)                                             |
| `pygpgo`                   | [Official](https://pygpgo.readthedocs.io/en/latest/)                                  |
| `pymoo`                    | [Official](https://pymoo.org/)                                                        |
| `pyopus`                   | [Official](https://fides.fe.uni-lj.si/pyopus/)                                        |
| `pypesto`                  | [Official](https://github.com/icb-dcm/pypesto)                                        |
| `pyriad`                   | [Official](https://pypi.org/project/pyriad/)                                          |
| `pysmac`                   | [Official](https://github.com/automl/pysmac)                                          |
| `pysot`                    | [Official](https://pysot.readthedocs.io/en/latest/)                                   |
| `pyswarms`                 | [Official](https://pyswarms.readthedocs.io/en/latest/)                                |
| `qiskit-optimization`      | [Official](https://pypi.org/project/qiskit-optimization/)                             |
| `rapids-NeurIPS`           | [Official](https://github.com/daxiongshu/rapids-ai-BBO-2nd-place-solution)            |
| `ray`                      | [Official](https://github.com/ray-project/ray)                                        |
| `rbfopt`                   | [Official](https://github.com/coin-or/rbfopt)                                         |
| `scikit-opt`               | [Official](https://github.com/guofei9987/scikit-opt)                                  |
| `scikit-optimize`          | [Official](https://scikit-optimize.github.io/stable/)                                 |
| `simanneal`                | [Official](https://github.com/perrygeo/simanneal)                                     |
| `simple`                   | [Official](https://github.com/chrisstroemel/Simple)                                   |
| `solidpy`                  | [Official](https://github.com/100/Solid)                                              |
| `spearmint`                | [Official](https://github.com/HIPS/Spearmint)                                         |
| `spotpy`                   | [Official](https://spotpy.readthedocs.io/en/stable/)                                  |
| `ssb-optimize`             | [Official](https://github.com/theleftcoast/swarm-simplex-bootstrap)                   |
| `swarm-cg`                 | [Github](https://github.com/GMPavanLab/Swarm-CG)                                      |
| `swarmlib`                 | [Official](https://pypi.org/project/swarmlib/)                                        |
| `swarmpackagepy`           | [Official](https://pypi.org/project/SwarmPackagePy/)                                  |
| `tgo`                      | [Official](https://github.com/stefan-endres/tgo)                                      |
| `turbo-NeurIPS`            | [Official](https://github.com/nphdang/turbo_bbo_neurips_2020)                         |
| `turbo`                    | [Official](https://github.com/uber-research/TuRBO)                                    |
| `ultraopt`                 | [GitHub](https://auto-flow.github.io/ultraopt/zh/)                                    |
| `yabox`                    | [GitHub](https://github.com/pablormier/yabox)                                         |
| `zoofs`                    | [GitHub](https://github.com/jaswinder9051998/zoofs)                                   |
| `zoopt`                    | [GitHub](https://github.com/polixir/ZOOpt)                                            |

# Notes

1- If you are having trouble while installing via `!pip install <PACKAGE>` (in-line code) or `pip install <PACKAGE>` (terminal code), you may use the following piece of code. Also, please be aware that some of the introduced packages require installing software or downloading and compiling a copy of their binary files to be imported into Python. Therefore, some of them are not easily `pip` installable.

```python
import pip

#Function:
def install(package):
    if hasattr(pip, 'main'):
        pip.main(['install', package])
    else:
        pip._internal.main(['install', package])

#Example:
install('pyomo')
```

2- There are some benchmarkig `tools` and websites, which are introduced as follows:

| Benchmark  | Link                                                     |
| ---------- | -------------------------------------------------------- |
| `humpday`  | [Official](https://www.microprediction.com/blog/humpday) |
| `pycutest` | [Official](https://github.com/jfowkes/pycutest)          |
| Mittelmann | [Official](http://plato.la.asu.edu/bench.html)           |
