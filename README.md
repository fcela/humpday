# humpday ![tests](https://github.com/microprediction/humpday/workflows/tests/badge.svg) ![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

A package that helps you choose a Python global optimizer package, and strategy therein, from [Ax-Platform](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/axcube.py), [bayesian-optimization](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/bayesoptcube.py), [DLib](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/dlibcube.py), [HyperOpt](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/hyperoptcube.py), [NeverGrad](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/nevergradcube.py), [Optuna](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/optunacube.py), [Platypus](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/platypuscube.py), [PyMoo](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/pymoocube.py), [PySOT](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/pysotcube.py), Scipy [classic](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/scipycube.py) and [shgo](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/shgocube.py), [Skopt](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/skoptcube.py),
[nlopt](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/nloptcube.py), 
and [UltraOpt](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/ultraoptcube.py). 
 
### 

- 50+ strategies are assigned [Elo ratings](https://github.com/microprediction/optimizer-elo-ratings/tree/main/results/leaderboards) by sister repo [optimizer-elo-ratings](https://github.com/microprediction/optimizer-elo-ratings). All are presented in a common calling syntax. By all means contribute more to [optimizers](https://github.com/microprediction/humpday/tree/main/humpday/optimizers). 
- Pass the dimensions of the problem, function evaluation budget and
 time budget to receive [suggestions](https://github.com/microprediction/humpday/blob/main/humpday/comparison/suggestions.py) that are independent of your problem set,

 - Or simply pass your objective function, and it will time it and do something sensible:
     
        from humpday import recommend
    
        def my_objective(u):
            time.sleep(0.01)
            return u[0]*math.sin(u[1])

        recommendations = recommend(my_objective, n_dim=21, n_trials=130)
        
- If you are feeling lucky, the [meta](https://github.com/microprediction/humpday/blob/main/humpday/optimizers/meta.py) minimizer which will
 choose an optimizer based only on dimension and number of function evaluations, then run it:   

        from humpday import minimize
        best_val, best_x = minimize(f, n_dim=13, n_trials=130 )
        
- Better yet, call [points_race](https://github.com/microprediction/humpday/blob/main/humpday/comparison/odious.py) on a list of your own objective functions:

        from humpday import points_race
        points_race(objectives=my_objectives,n_dim=5, n_trials=100)
        
Here *f* is intended to be minimized on the hypercube [0,1]^n_dim.  

![](https://i.imgur.com/FCiSrMQ.png)
 
### Optimizer suggestions

        from pprint import pprint 
        from humpday import suggest
        pprint(suggest(n_dim=5, n_trials=130,n_seconds=5*60))

where *n_seconds* is the total computation budget for the optimizer (not the objective function) over all 130 function evaluations. Alternatively you can pass
an objective function:


As this function is very fast, some optimizers will be culled from the list.   

### Install

    pip install humpday
    
Bleeding edge:

    pip install git+https://github.com/microprediction/humpday
  
File an issue if you have problems. If you get a CMake error, try:

    pip install cmake
    pip install humpday 

#### Optional packages

Install directly if you want them to be included:

    pip install cmake
    pip install ultraopt
    pip install hyperopt
    
### Articles 

- (most recent) [HumpDay: A Package to Take the Pain Out of Choosing a Python Optimizer](https://www.microprediction.com/blog/humpday). 
- [Comparing Python Global Optimizers](https://www.microprediction.com/blog/optimize).

