Table of Contents
===================
- [Optimization for Training Deep Models](#optimization-for-training-deep-models)
- [Learning v/s Optimizing](#learning-v-s-optimizing)
  * [Emperical Risk](#emperical-risk)
  * [Disadvantages of Emperical Risk Method](#disadvantages-of-emperical-risk-method)
- [Surrogate Loss Function and Early Stopping](#surrogate-loss-function-and-early-stopping)
  * [Difference between Genral Optimization and Optimizing Training Algorithms](#difference-between-genral-optimization-and-optimizing-training-algorithms)
- [Batch and Mini-batch Algorithms](#batch-and-mini-batch-algorithms)
  * [Various Information extracted from Batch/Minibatch Algorithms](#various-information-extracted-from-batch-minibatch-algorithms)
  * [Batch v/s Minibatch](#batch-v-s-minibatch)
- [Challenges in Neural Network Optimization](#challenges-in-neural-network-optimization)
  * [Ill-Conditioning](#ill-conditioning)
  * [Local Minima](#local-minima)
  * [Plateaus, Saddle Points and Other Flat Regions](#plateaus--saddle-points-and-other-flat-regions)
    + [Properties Observed of Random Functions w.r.t Eigen Values](#properties-observed-of-random-functions-wrt-eigen-values)
  * [Cliﬀs and Exploding Gradients](#cli-s-and-exploding-gradients)
  * [Long Term Dependencies](#long-term-dependencies)
    + [Sample Scenario describing Exploding Gradient Problem](#sample-scenario-describing-exploding-gradient-problem)
- [Basic Algorithms](#basic-algorithms)
  * [Stochastic Gradient Descent (SGD)](#stochastic-gradient-descent--sgd-)
  * [Momentum](#momentum)
  * [Nesterov Momentum](#nesterov-momentum)
- [Algorithms with Adaptive Learning Rate](#algorithms-with-adaptive-learning-rate)
  * [AdaGrad](#adagrad)
  * [RMSProp](#rmsprop)
  * [Adam](#adam)
- [Approximate Second-Order Methods](#approximate-second-order-methods)
  * [Newton's Method](#newton-s-method)
  * [Conjugate Gradients](#conjugate-gradients)
    + [Problem Statement](#problem-statement)
    + [Solution](#solution)
- [Broyden–Fletcher–Goldfarb–Shanno (BFGS) Algorithm](#broyden-fletcher-goldfarb-shanno--bfgs--algorithm)
  * [Limited Memory BFGS (L-BFGS)](#limited-memory-bfgs--l-bfgs-)
- [Optimization Strategies and Meta-Algorithms](#optimization-strategies-and-meta-algorithms)
  * [Batch Normalization](#batch-normalization)
    + [Problem Statement](#problem-statement-1)
    + [Solution](#solution-1)
  * [Batch Transformation](#batch-transformation)
  * [Coordinate Descent](#coordinate-descent)
  * [Polyak Averaging](#polyak-averaging)
  * [Supervised Pretraining](#supervised-pretraining)
  
# Optimization for Training Deep Models
# Learning v/s Optimizing
* Machine learning acts **indirectly** by trying to **optimize performance measure, P,** defined w.r.t test set.
* Goal of learning is to reduce **expected generalization errror.**
* Learning algorithms **reduce cost functions**
    * By **minimizing expected loss** on training data set.
    * In the hope that **indirect optimization will improve performance.**
* Expectation is taken across **data-generating distribution**, rather than finite training set.<br>
<img src='./images/01.cost_function_for_entire_data_set.png'></img>

## Emperical Risk
* Simplest way to **convert ML problem to an optimization problem** is to **minimize expected loss** on the training set.
* Replacing **true distribution p(x, y)** with **empirical distribution ˆp(x, y)** deﬁned by the training set.<br>
<img src='./images/02.emperical_risk.png'></img>
* **m** is number of training examples.
* Training process based on **minimizing average training error** is known as **empirical risk minimization**.
* Rather than **optimizing risk directly, optimize empirical risk** and hope that **risk decreases signiﬁcantly** as well.

## Disadvantages of Emperical Risk Method
* Prone to **over-fitting.**
* Models with **high capacity** can **memorize** training data.
* Most effective loss functions are based on **SGD**, but losses like **0-1 loss have no useful derivatives.**

# Surrogate Loss Function and Early Stopping
* In situations where loss function is **difficult to/cannot be optimized,** we optimize **surrogate loss function**, acting as proxy with several advantages -
    * Differentiable
    * Improves robustness.
## Difference between Genral Optimization and Optimizing Training Algorithms
*  **Training algorithms** do not usually halt at a local minimum. ML algorithm **minimizes surrogate loss function** and halts when **convergence criterion based on early stopping** is satisﬁed.
* Training **halts** while the surrogate loss function **still has large derivatives.**

# Batch and Mini-batch Algorithms
* **Objective function** usually **decomposes as a sum** over training examples.
* **Optimization** in ML, typcally computes loss and updates parameters **iteratively**, e.g. **stochastic gradient descent.**
* Computing **exact expectation**/ **using entire training set** (batch/deterministic algorithm) can be **computationally expensive.**
* Minibatch algorithms compute expectation by **randomly sampling small number of examples** from dataset, then taking the average over only those examples.

## Various Information extracted from Batch/Minibatch Algorithms
* Second order methods **that use Hessian matrix,** require much **larger batch sizes.**
* Minibatches should be **sampled randomly.**
* **Minibatch SGD** follows gradient of **true generalization error**, as long as **no examples are repeated**.
* When using an **extremely large training set**, **underﬁtting** and **computational eﬃciency** becomes the predominant concerns.

## Batch v/s Minibatch
* Each iteration in **minibatch** may have **poor optimization performance** than batch algorithm.
* However, after **many iterations**,mini-batch algorithm generally **converges to optimal state.**
<img src="./images/03.batch_vs_minibatch.png"></img>

# Challenges in Neural Network Optimization
## Ill-Conditioning
* Arises due to **ill-conditioning of Hessian matrix, H.**
* **SGD gets stuck** i.e. even very **small steps increase cost function.**
* 2nd order **Taylor series of cost function** predicts that gradient step of  −ε**g** will **add following term to cost**.<br>
<img src="./images/04.ill_conditioning.png"></img>
* **Ill conditioning in Taylor-Series** occurs when:<br>
<img src="./images/05.ill_conditioing_in_taylor_series.png"></img>

## Local Minima
* If **starting point** of gradient descent was chosen **inappropriately**, a non-convex fucntion **cannot reach global minimum.**<br>
<img src="./images/05.issue_with_local_minima.png"></img>

## Plateaus, Saddle Points and Other Flat Regions
* In non-convex functions, **local minima are rare** as compared to other **zero gradient point called saddle points.**
* At **saddle point**, **Hessian matrix** has both **positive and negative eigenvalues**.
* **Cost (+) > Cost( saddle point ) > Cost (-)**<br>
   * Cost (+) : Cost of points lying on **+ve eigen vectors**.<br>
   * Cost (-) : Cost of points lying on **-ve eigen vectors**
* Sample **saddle point in a deep neural network** is shown below<br>
<img src="./images/06.saddle_point.png"></img>

### Properties Observed of Random Functions w.r.t Eigen Values
* In higher-dimensional spaces, **local minima are rare**, and **saddle points are more common.**
* **Eigenvalues** of Hessian become **more likely to be positive** as we reach regions of **lower cost.**
* **Local minima** are much more likely to **have low cost** than high cost.
* **Critical points** with **high cost** are far more likely to be **saddle points.**
* **Critical points** with **extremely high cost** are more likely to be **local maxima.**

## Cliﬀs and Exploding Gradients
* **Neural networks with many layers** often have extremely steep regions resembling **cliﬀs,** resulting due to **multiplication of  several large weights together.**<br>
<img src="./images/07.cliffs.png"></img>
* **Gradient doesnot specify optimal size** but specifies **optimal direction withinan inﬁnitesimal region.**
* When **traditional gradient descent** algorithm proposes **making a very large step :**
     * **Gradient Clipping** interevens
     * Reduces **step-size**
     *  making it **less likely to go outside** the region where gradient indicates **direction of approximately steepest descent.**
 * Following is an example of **Gradient Clipping for Handling Cliffs**<br>
 <img src="./images/08.gradient_clipping.png"></img>
 
## Long Term Dependencies
* Computational graph becomes **extremely deep.**
* **Repeated application of same parameters** gives rise to especially pronounced diﬃculties.
### Sample Scenario describing Exploding Gradient Problem
* Computational graph containing path that consists of **repeatedly multiplying by a matrix W,** which after **t-steps** is equivalent to **multiplying by**  <img src="./images/09.wt.png"></img> --<br>
   * <img src="./images/10.wt_expansion.png"></img><br>
   * If **λi > 1**, *explosion,* makes learning **unstable**<br>
   * If **λi < 1**, *vanish,*, make it **diﬃcult to know which direction** parameters should move **to improve cost function**
   
# Basic Algorithms

## Stochastic Gradient Descent (SGD)
* **Unbiased estimate** of gradient can be calculated by taking **average gradient on a minibatch** of **m examples** drawn i.i.d from the data-generating distribution.
* **Crucial parameter** for the SGD algorithm is the **learning rate.**
* **Learning rate** should be **decayed** with time until iteration **τ**.<br>
<img src="./images/12.learning_rate_decay.png"></img><br>
* **Suﬃcient condition** to guarantee **convergence of SGD** is<br>
<img src="./images/11.sgd_convergence.png"></img><br>
* <img src="./images/13.et.png"></img> should be set to **1% of** <img src="./images/14.e0.png"></img><br>
* If value of  <img src="./images/14.e0.png"></img> is -
      * **too high,** curve shows **violent oscillations**, cost function **increases.**
      * **too low,** curve can get **stuck in high cost value.**
* **Batch gradient descent** enjoys **better convergence rates** than stochastic gradient descent in theory.
* **Gradient Formula**<br>
<img src="./images/15.gradient.png"></img>
* **Updation Formula**<br>
<img src="./images/16.update.png"></img>

## Momentum
* Momentum method is designed to **accelerate learning.**
* Accumulates an **exponentially decaying moving** average of past gradients and continues to move in their direction.
* Below is comparison of **graident descent with and without momentum** -<br>
<img src="./images/17.gd_with_without_momentum.png"></img>
* **Update rule** in momentum method is given by -<br>
<img src="./images/18.update_for_momentum.png"></img>
* **Accumulate velocity**- <br>
<img src="./images/19.accumulate_velocity.png"></img>

## Nesterov Momentum
* **Gradient** is evaluated **after current velocity** is applied.
* Attempt to **add a correction factor** to the standard method of momentum.
* Comparison between **standard momentum and Nesterov momentum methods** are given as follows -<br>
<img src="./images/21.comparison_p_vs_np.png"></img>
* **Update rule**<br>
<img src="./images/20.nestrov_momentum_update.png"></img>

# Algorithms with Adaptive Learning Rate
## AdaGrad
* **Adaptive Gradient** is a modified SGD with **per-parameter learning rate.**
    * **Increases learning rate** for parameters having **small gradient.**
    * **Decreases learning rate** for parameters having **large gradient.**
 * **Gradient** for AdaGrad is given by -<br>
 <img src="./images/22.grad_update_for_adagrad.png"></img>
 * **Accumulate Squared Gradients**<br>
 <img src="./images/23.accumulate_adagrad.png"></img> <br>
 * **Apply Update**<br>
  <img src="./images/24.update_adagrad.png"></img> 

## RMSProp
* **Root Mean Square Propagation** is modified version of **AdaGrad.**
* Modifies **Gradient accumulation** to **exponentially weighted moving average.**
* **Gradient -**<br>
 <img src="./images/25.rmsprop_gradient.png"></img> 
 * **Accumulate Squared Gradients -**<br>
 <img src="./images/26.accumulate_rmsprop.png"></img> 
 * **Apply update -**<br>
 <img src="./images/27.update_rmsprop.png"></img>

## Adam
* Combination of **RMSProp and momentum.**
* Accumulate **first and second order moment estimates -**<br>
 <img src="./images/28.momentum_update_adam.png"></img>
* Correct **bias in 1st and 2nd order moments -**<br>
  <img src="./images/29.bias_update_adam.png"></img>
* **Apply update -**<br>
  <img src="./images/30.final_update_adam.png"></img>

# Approximate Second-Order Methods
## Newton's Method
* Optimization scheme based on **second-order Taylor series expansion** to approximate **J(θ)** near some point θ0, **ignoring derivatives of higher order.**<br>
 <img src="./images/31.taylor_expansion.png"></img>
* **Newton parameter update rule** is given by -<br>
 <img src="./images/32.update_rule_newton.png"></img>
* Newton’s method can be **applied iteratively,** as long as Hessian remains **positive deﬁnite.**
* Hessian matrix can be **regularized, as below** incase eigen values of Hessian matrix are **not positive definite**, Newton's method can **cause updates to move in wrong direction.**<br>
 <img src="./images/33.regularized_newton.png"></img>
 * **Disadvantages of Newton's Method:**<br>
      * Huge computational **cost.**
      * Computational **complexity** of <img src="./images/34.computational_complex_newton.png"></img>
      * Networks with **very small number of parameters** can be practically trained via Newton's method.
      
## Conjugate Gradients

* Method to **eﬃciently avoid calculation of inverse Hessian** by iteratively descending conjugate directions.
* **Current line search direction**, is guaranteed to be **orthogonal to previous line search direction.**

### Problem Statement
By **following gradient** at end of each line search we are **undoing progress we have already made in the direction of the previous line search.**
 <img src="./images/35.congugate_directions.png"></img>
### Solution 
* We seek to ﬁnd a **search direction** that is **conjugate to previous** line search direction.
* At iteration *t*, direction, next search direction will be of the form -<br>
<img src="./images/36.congugate_solution.png"></img>
* <img src="./images/37.bt.png"></img> magnitude controls how much of direction, <img src="./images/38.dt_1.png"></img>,
we should **add back to current search direction.**
* Two directions <img src="./images/39.dt.png"></img> and <img src="./images/38.dt_1.png"></img>  are said to be **orthognal** iff -<br>
<img src="./images/40.conjugates.png"></img> 
* Two methods to compute value of <img src="./images/37.bt.png"></img> are -<br>
<img src="./images/41.bt_computation.png"></img> 

# Broyden–Fletcher–Goldfarb–Shanno (BFGS) Algorithm
* Similar to **conjugate gradient** method plus additional advantages of **Newton's method.** 
* Problem with **Newton's method** was **finding inverse of Hessian matrix,** which was later approximated using matrix, <img src="./images/42.mt.png"></img> , which is iteratievely refined using **low-rank updates**.
* Success of BFGS  is **not heavily dependent** on line search **ﬁnding a point very close to true minimum** along the line.
* Hence, BFGS acn spend **less time reﬁning each line search.**
* BFGS should **store inverse Hessian matrix**, hence it requires, <img src="./images/43.memory_space_BFGS.png"></img> memory.
* **Solution** to above problem statement is given by **L-BFGS**

## Limited Memory BFGS (L-BFGS)
* Memory cost of BFGS can be avoided by **not storing inverse of Hessian matrix.**
* Computes **approximation M** using same method as BFGS algorithm but **beginning with the assumption that M(t−1) is identity matrix**, rather than storing approximation from one step to next.
* Can be used to store **more information about matrix M**, which costs only **O(n) per step.**


# Optimization Strategies and Meta-Algorithms
## Batch Normalization
### Problem Statement
In very deep models, involving several composition of layers, **gradient** tells how to **update each parameter**, assuming that **other layers do not change.**

### Solution
* Batch normalization provides a way of **reparametrizing almost any deep network.**
* BN **normalizes** each layer's input of a given **mini-batch** as follows -<br>
<img src="./images/44.batch_normalization.png"></img>
* Normalization operation **removes effect** of any action t**hat can increase standard deviation/mean.**

## Batch Transformation
* Simply normalizing each input of a layer may change what the layer can represent.
* Therefore, we need to introduce **linear transformation** for each activation function -<br>
* γ,β are **learned at each step**, where -
<img src="./images/45.batch_transformation.png"></img>
   * **γ** : scale factor
   * **β** : shift factor
* Below is an example of Neural Network **with and without Batch Normalization** -<br>
<img src="./images/46.comparison_bw_bn_nonbn.png"></img>

## Coordinate Descent
* Solving an optimization problem  quickly by **breaking it into separate pieces.**
* Given a **function f(x)**, minimize it first w.r.t **x1**, then w.r.t x2 and so on, to **eventually arrive at local minimum.**
* This approach is called **coordinate descent**, since we are **optimizing one coordinate at a time.**
* **Not a very good strategy** when **value of one variable strongly inﬂuences** optimal value of another variable.

## Polyak Averaging
* **Averaging several points** in the trajectory through parameter space visited by an optimization algorithm.
* This approach has **strong convergence guarentee** in case of some problems such as **SGD applied to convex problems.** 
* When applying **Polyak averaging to nonconvex problems**, we use an **exponentially decaying running average-**<br>
<img src="./images/47.polyak_averaging_noncovex.png"></img>

## Supervised Pretraining
* Basic idea is to - **train model to solve a simpler task, then move on to confront the ﬁnal task.**
* Strategies involving **training models on simple tasks before confronting the model to perform final task** is called **pretraining.**
* Approach to **break supervised learning problems** into other **simpler supervised** learning problems is known as **greedy supervised pretraining.**
* Below is an example demonstrating **supervised pre-training.**<br>
<img src="./images/48.supervised_pretraining.png"></img>

[Back to top](#optimization-for-training-deep-models)









