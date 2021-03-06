# Probability and Information Theorey

Table of Contents
====================
* [Overview](#Overview)
* [Definitions and Formulas](#Definitions-and-Formulas)

# Overview
* Probability provides means to quantify uncertainity.
* Probability is used for 2 reasons in AI -
  * Model explaiability
  * Behaviour analysis of AI model

# Definitions and Formulas

| S.No. | Term/Formula                                        | Description                                                                                                                                                                                                               |
|-------|-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1.    | **Random Variable**                                     |Variable that can take **different values randomly**.<br> **Discrete Random Variable** has finite/counatably infinite states.<br>**Continous Random Variable** is associated with real value                                                 |
| 2.    | **Probability Distributions**                           | Describes how likely a **random variable takes each of its possible states**                                                                                                                                                  |
| 3.    | **Probability Mass Function  (PMF)**; *P(x)*             | Probability distributions over **discrete variables**.<br> Mapping from **state** of random variable to **probability** of that variable taking that state.                                                                              |
| 4.    | **Joint Probability  Distribution**, *P(X=x, Y=y)*        | Probability distribution over **different variables** at the same time.<br><img src="images/3.jpd_1.png" width="240" height="45" >                                                                                                                                                       |
| 5.    | **Properties of Joint Probability Distribution**        |Domain of P must be all possible states of x.<br><img src="images/1.uniform_distribution.png" width="250" height="75" >                                                                                                                                                                          |
| 6.    | **Uniform Distribution**                                |<img src="images/2.jpd_2.png" width="230" height="50" >                                                                                                                                                                                                                           |
| 7.    | **Probability Distribution Function**                   |PMF for **continous variables**.                                                                                                                                                                                          |
| 8.    | **PDF**; *x lies between [a, b]*                         |<img src="images/4.pdf_interval.png" width="250" height="50" >                                                                                                                                                                                                                           |
| 9.    | **Marginal Probability**                                |Probability **distribution over subset**.<br><img src="images/5.Marginal_prob.png" width="320" height="70" ><br><img src="images/6.Marginal_prob_continous.png" width="270" height="60" >                                                                                                                                                                                     |
| 10.   | **Conditional Probability**                             |**Probability** of an event, **given some other event** has already happened.<br>**Conditional Probability** valid only when **P(X=x)>0**.<br><img src="images/7. Conditional_prob.png" width="270" height="60" >                                                                                                |
| 11.   | **Chain Rule for Conditional  Probability**             |<img src="images/8.Chain_Rule.png" width="380" height="60" >                                                                                                                                                                                                                           |
| 12.   | **Indipendence Rule**                                   |<img src="images/9.Indipendence_Rule.png" width="340" height="60" >                                                                                                                                                                                                                           |
| 13.   | **Conditional Indipendence**                            |<img src="images/10.Conditional_Indipendence.png" width="420" height="80" >                                                                                                                                                                                                                           |
| 14.   | **Expectation**                                         |<img src="images/11.Expectation.png" width="270" height="60" ><br><img src="images/12.Expectation_for_continous_variables.png" width="270" height="60" ><br><img src="images/13.Rules_of_expectation.png" width="320" height="60" >                                                                                                                                                                                                                            |
| 15.   | **Variance**                                            |Measures how much **values of function of random variable x vary** as we sample different values of x.<br><img src="images/14.Variance.png" width="270" height="60" >                                                                                                                       |
| 16.   | **Standard Deviation**                                  | Square root of **Variance**.                                                                                                                                                                                                                           |
| 17.   | **Co-variance**                                         |Sense of **how much 2 variables are linearly related** to each other.<br><img src="images/15.Covariance.png" width="340" height="60" >                                                                                                                                                        |
| 18.   | **Properties of  Co-variance**                          |co-variance **== 0** => indipendent variables<br>co-variance **!= 0** => dependent variables                                                                                                                                     |
| 19.   | **Co-variance matrix**                                  |<img src="images/16.Covariance_matrix.png" width="270" height="60" ><br><img src="images/17.Covariance_matrix_2.png" width="270" height="60" >                                                                                                                                                                                                                           |
| 20.   | **Bernoulli Distribution**                              |Distribution over **single binary random variable**.<br> Gives probability of random variable being equal to 1.<br><img src="images/18.Bernoulli_distribution.png" width="270" height="160" >                                                                                                                |
| 21.   | **Multinoulli Distribution**                            |Distribution over **single binary random variable with k(finite) different states.**<br><img src="images/19.Multinoulli_distribution.png" width="200" height="40" ><br><img src="images/20.Multinoulli_conditions.png" width="200" height="40" >                                                                                                                                        |
| 22.   | **Gaussian (Normal) Distribution**                      |<img src="images/22.Gaussian_distribution.png" width="320" height="50" ><br>Parameters **controlling normal distribution** : <img src="images/21. Parameters_controlling_normal_distribution.png" width="130" height="30" > <br>**μ** gives coordinates of **central peak**                                                                                                                                     |
| 23.   | **Precision (Inverse Variance)**                        |<img src="images/23.Precision.png" width="320" height="50" >                                                                                                                                                                                                                           |
| 24.   | **Standard Normal Distribution**                        |<img src="images/24.Standard_Normal_Distribution.png" width="350" height="190" >                                                                                                                                                                                                                           |
| 25.   | **Central Limit Theorem**                               |Sum of **indipendent random variables** is approximately normal distributed.                                                                                                                                                  |
| 26.   | **Why Normal Distribution is a better default choice?** |**Central Limit theorem**; complicated systems can be modelled as normally distribued  noise.<br>It encodes **maximum amount of uncertainity** over real numbers                                                                  |
| 27.   | **Multivariate Normal Distribution**                    |<img src="images/25.Multivariate_distribution.png" width="350" height="100" ><br>∑ gives **co-variance distribution**.                                                                                                                                                                                        |
| 28.   | **Precision Matrix**                                    |<img src="images/26.Precision_matrix.png" width="350" height="100" >                                                                                                                                                                                                                           |
| 29.   | **Exponential Distribution**                            |To achieve **probability distribution with sharp point** at x=0.<br><img src="images/27.Exponential_Distribution.png" width="250" height="80" ><br>Uses **Indicator fucntion**, to assign probability 0, to all -ve numbers.<br><img src="images/28.Indicator_function.png" width="150" height="50" >                                                                                      |
| 30.   | **Laplace Distribution**                                |Places **sharp peak of probability mass** at any **arbitrary** point u.<br><img src="images/29.Laplace.png" width="320" height="100" >                                                                                                                                                         |
| 31.   | **Dirac Distribution**                                  |Specifies **all mass in probability distribution** cluster around **single point**.<br>**Zero** valued everywhere, except 0, yet integrates to 1.<br>Generalized function that puts **less density on all points other than 0.**<br><img src="images/30.Dirac_delta.png" width="200" height="50" >           |
| 32.   | **Emperical Distribution**                              |Puts probability **mass of (1/m)** on each masses.<br><img src="images/31.Emperical.png" width="320" height="100" >                                                                                                                                                                          |
| 33.   | **Mixture of Distributions**                            |On each trial, **choice of which component distribution** should generate sample by  generating component identity from **multinouli distribution**-<br><img src="images/32.Multinouli_distribution.png" width="320" height="100" >                                                                           |




| S.No. | Term/Formula             | Description                                                                                                                                                                                                               |
|-------|--------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 33.   | **Mixture of Distributions** | * On each trial, choice of which component distribution should generate sample by  generating component identity from **multinouli distribution**-<br><img src="images/32.Multinouli_distribution.png" width="320" height="100" >                                                                           |
| 34.   | **Gaussian Mixture Model**   |Each component has **separately parameterized mean and co-variance**.<br>Specifies **prior probability** given to each component i.<br><img src="images/33.Gaussian_mixture.png" width="150" height="50" ><br>Expresses model's belief **about c, before it has observed x** |
| 35.   | **Posterior Probability**    |Probability is computed **after observation of x**.<br><img src="images/35.Posterior_probability.png" width="150" height="30" >                                                                                                                                                                         |
| 36.   | **Universal Approximator**   |Any **smooth density** can be approximated with any specific **nonzero amount of error** by Gaussian mixture model with enough components.                                                                                     |
| 37.   | **Logistic Sigmoid**         |Produces **φ paramter of Bernoulli distribution**<br>**Range** - (0,1).<br><img src="images/36.Sigmoid_function.png" width="240" height="80" ><img src="images/37.Sigmoid_graph.png" width="320" height="150" >                                                                                                                                                        |
| 38.   | **Softplus Function**        |Produces **β or α paramters of Normal distribution**.<br>**Range** - (0, infinity).<br><img src="images/38.Softplus_function.png" width="200" height="50" ><img src="images/39.Softplus.png" width="200" height="50" >                                                                                                                                               |
| 39.   | **Properties of Softplus**   |<img src="images/40.Softplus_graph.png" width="320" height="100" ><img src="images/41.Properties_of_softplus.png" width="380" height="300" >                                                                                                                                                                                                                            |
| 40.   | **Baye's Rule**              |<img src="images/42.Baeyes.png" width="200" height="50" >                                                                                                                                                                                                                           |
| 41.   | **Measure Zero**             |Rigrous way of describing that **set of points is negligibly small**.<br>Set of measure 0 occupies **no volume in space** we are measuring.                                                                                       |
| 42.   | **Almost Everywhere**        |Property that **holds almost everywhere** holds throughout all space **except for on the set of measure 0**.                                                                                                                    |




# Information Theorey
Information theory is a branch of applied mathematics that revolves around quantifying how much information is present in a signal.<br>
The basic intuition behind information theory is that learning that an **unlikely event has occurred** is **more informative** than learning that a **likely event has occurred**.

## Rules to Quantatify Information
* Less likely event should have low information content.
* More likely event should have more information content.
* Indipendent events should have additive information.

## Self Information
* Self information satisfies all 3 rules that is needed to quantify information.<br><img src="images/43.self_information.png" width="200" height="50" >
* *I(x)* is written in units of **nat.**
* **One Nat** is amount of information gained by observing event of probability *(1/e).*
* **Bits/Shannons** is self-information with log base 2.
* Deals with onle single outcome.
* **Shannon Entropy** is expected amount of information drawn from probability distribution.<br><img src="images/44.Shannon_entropy.png" width="320" height="70" >

## Kullback-Leibler (KL) Divergence
KL Divergence is used to measure difference between 2 separate probability distribution *P(x)* and *Q(x)* over same random variable *x*.<br><img src="images/45.KL_divergence.png" width="350" height="90" >

### Properties of KL Divergence
* Non-negative.
* KL divergence = 0; iff *P* and *Q* are same distribution/ equal "almost everywhere" in case of discrete/continous variables.
* Because of the above 2 properties, it is conceptualized as distance between the 2 distributions.
* <img src="images/46.KL_properties.png" width="200" height="50" >

## Cross Entropy
* Closely related to KL divergence.
* Minimizing cross entropy w.r.t. Q is same as minimizing KL divergence.
<img src="images/47.Cross_entropy.png" width="200" height="50" >

## Structured Probabilistic Models
Representing probability distribution over 3 variables as product of probability distribution over 2 variables.
<img src="images/47.Cross_entropy.png" width="200" height="50" >
* Greatly reduces cost of representing distribution.

### Types of Structured Probabilistic Models
**Directed Models**
* Graphs with directed edges
* Represent factorization into conditional probability distribution.
* Contains of 1 factor for every random variable *Xi*
* Factor consists of conditional probability distribution over Xi, given its parents.<br>
<img src="images/49.Directed_graphs.png" width="200" height="50" ><br>
* Example of directed graph -<br>
<img src="images/50.Directed_graph_2.png" width="320" height="250" ><br>
<img src="images/51.Directed_graph_3.png" width="400" height="100" ><br>

**Undirected Models**
* Graphs with undirected edges.
* Set of nodes connected to each other in graph is called *Clique*.
* Output of each factor is non-negative.
* No constraint that sum of factors must integrate to 1.
* To obtain normalized distribution, divide by *Z* (normalizing constant).<br>
<img src="images/52.Normalizing_constant.png" width="220" height="70" ><br>
* Example of undirected graph - <br>
<img src="images/53.Undirected_graph.png" width="320" height="250" ><br>
<img src="images/54.Undirected_graph_2.png" width="400" height="100" ><br>



