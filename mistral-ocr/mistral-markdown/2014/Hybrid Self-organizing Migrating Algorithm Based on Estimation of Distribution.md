# Hybrid Self-organizing Migrating Algorithm Based on Estimation of Distribution 

LIN Zhi-yi<br>Faculty of Computer<br>Guangdong University of Technology<br>Guangzhou, China<br>e-mail: lzy291@gdut.edu.cn

WANG li-juan<br>Faculty of Computer<br>Guangdong University of Technology<br>Guangzhou, China<br>e-mail: ljwang@gdut.edu.cn


#### Abstract

A new hybrid self-organizing migrating algorithm based on estimation of distribution (HSOMA) is proposed to resolve the defect of premature convergence in the self-organizing migrating algorithm (SOMA) and improve the search ability of SOMA. In order to make full use of the statistical information on population and increase the diversity of migration behavior, HSOMA introduces the thought of estimation of distribution algorithm (EDA) into SOMA and reproduces the genes of new individuals by both SOMA and EDA. The proportion of the use of two algorithms is decided by a control parameter. In this way, HSOMA can increase the population diversity and improve the convergence speed. HSOMA is tested on several complex benchmark functions taken from literature and its efficiency is compared with SOMA, the continuous domain PopulationBased Incremental Learning algorithm(PBILe) and hybrid migrating behavior based self-organizing migrating algorithm(HBSOMA). On the basis of comparison it is concluded that HSOMA shows better global search ability and convergence accuracy.


Keywords- self-organizing migrating algorithm; estimation of distribution algorithm; premature convergence; population diversity; function optimization

## I. INTRODUCTION

Self Organizing Migrating Algorithms (SOMA) is developed by Zelinka and Lampanin based on the competitive-cooperative behavior of intelligent creatures ${ }^{[1]}$. The advantages of SOMA over other evolutionary algorithms, like simple structure, few control parameters, have made it a popular stochastic optimizer. SOMA has been successfully applied to a whole host of optimization problems, such as reliability-redundancy allocation ${ }^{[2]}$, Chaotic System Control ${ }^{[3]}$, Neural Network Synthesis ${ }^{[4]}$, Multi-Objective optimization ${ }^{[4]}$ and flow-shop scheduling ${ }^{[5]}$. However, similar to evolutionary algorithms, SOMA has the defect of premature convergence during the evolution.

Several attempts have been made to overcome the defect of premature convergence about SOMA in recent years. One import strategy is to reduce the probability by adding other operator or adjust algorithm's parameters. For example, L. D. S. Coelho ${ }^{[2]}$ had used a Gaussian operator to improve the local search ability of SOMA, LIN Zhi-yi et. al. developed a modified SOMA based on Oppositionbased learning ${ }^{[6]}$, SINGH D et. al. proposed a novel SOMA by using Non Uniform mutation operator ${ }^{[7]}$.

However, according to the "no free lunch" theorem, every algorithm has its specific application range, so the effect of this strategy is limited. Another import strategy is combine SOMA with other optimization algorithms to form hybrid SOMA, such as differential evolution algorithm(DE) ${ }^{[8]}$, cultural algorithm ${ }^{[9]}$, and genetic algorithm(GA) ${ }^{[3]}$. Hybrid SOMA approaches have shown promising performance on optimization problems, mainly because they can benefit from the advantages of both SOMA and other algorithms. However, hybrid SOMA has no mechanism to extract and use global information about the search space.

Therefore, in order to prevent premature convergence and improve the search ability of SOMA, a novel hybrid self-organizing migrating algorithm based on estimation of distribution (HSOMA) is proposed in this paper. In HSOMA, part of a new individual is generated by SOMA algorithm, but the other part is sampled by EDA algorithm. In this way, the local information of best individual and the global information are used to guide the search. The proposed algorithm is tested on several benchmark functions and also compared with other three optimization algorithms.

This paper is organized as follows. Section II provides full details of the proposed HSOMA. Section III compares HSOMA with other methods on a set of test problems. Finally, Section IV presents the conclusion remarks.

## II. HYBRID SELF-ORGANIZING MIGRATING ALGORITHM BASED ON ESTIMATION OF DISTRIBUTION

## A. self-organizing migrating algorithm (SOMA)

SOMA works on a population of candidate individuals in loops called migration loops. In each loop, the population is evaluated, and the individual with highest fitness is known as the Leader $L$. Apart from the leader $L$, in one migration loop, all individuals will traverse a certain distance(called the PathLength) towards the leader in n steps of defined length. The movement of an individual during the migration is given as follows ${ }^{[1]}$ :

$$
X_{i, j}^{M L+1}=X_{i, j, \text { start }}^{M L}+\left(X_{L, j}^{M L}-X_{i, j, \text { start }}^{M L}\right) * t^{*} P R T V e c t o r_{i} \quad(1)
$$

where $M L$ is the number of current migration loop, $X_{i, j, \text { start }}^{M L}$ is the original position of $i$ th individual in current migration loop, $X_{i, j}^{M L+1}$ is the new position for the $i$ th individual, in step $t$ in next migration loop $M L+1, X_{L, j}^{M L}$ is the position of the Leader in migration loop ML. $t \in[0$,

pathLength], $t=0$, Step, $2 *$ Step $_{t-1}$, PRT is an random number in $[0,1]$, and PRTVector is the control vector for the perturbation, which is generated according to the following expression.

$$
\text { PRTVector }_{j}=\left\{\begin{array}{ll}
1 & \text { if } r n d_{j}<P R T, \\
0 & \text { otherwise }
\end{array} \quad j=1,2, \mathrm{~L}, D\right.
$$

where $r n d_{j}$ is a random number with uniform distribution in range $[0,1]$ and $D$ is the number of decision variables. Further information about SOMA can be found at [1].

## B. Estimation of distribution algorithm (EDA)

The template is used to format your paper and style the text. All margins, column widths, line spaces, and text fonts are prescribed; please do not alter them. You may note peculiarities. For example, the head margin in this template measures proportionately more than is customary. This measurement and others are deliberate, using specifications that anticipate your paper as one part of the entire proceedings, and not as an independent document. Please do not revise any of the current designations.

Estimation of distribution algorithms(EDAs) are stochastic optimization techniques that explore the space of potential solutions by building and sampling explicit probabilistic models of promising candidate individuals[10]. The continuous domain Population-Based Incremental Learning algorithm (PBILc) ${ }^{[11]}$ is one of EDAs, which employs a model of a Gaussian distribution on the search space. Let $\operatorname{Pop}(t)$ be the population of individuals at generation $t$ and $n$ is the dimensions of a problem. PBILc works in the following iterative way:

Step1: Initialization. Initialize the algorithm parameters and the initial population $\operatorname{Pop}(0), t=0$.

Step2: Selection. Select M promising individuals from $\operatorname{Pop}(t)$ to form the parent set $Q(t)$ by the truncation selection.

Step3: Modeling. Construct probabilistic model $p(X)$ based on $Q(t)$. The probabilistic model of $t$-th generation $p_{t}(X)$ can be expressed as follows:

$$
p_{t}(X)=\prod_{i=1}^{n} \frac{1}{\sqrt{2 \pi \sigma_{i}^{2}}} e^{-\left(\sum_{i=1}^{n} \frac{X_{i}^{2}-\mu_{i}^{2}}{\sigma_{i}^{2}}\right)^{2}}
$$

The mean and the standard deviation can be estimated as follows:
if $t=0$ then

$$
\mu_{i}^{t}=\sum_{i=1}^{M} X_{i}^{t} / M, \quad \sigma_{i}^{t}=\sqrt{\sum_{i=1}^{M}\left(X_{i}^{t}-\mu_{i}^{t}\right)^{2} / M}
$$

else

$$
\begin{aligned}
& \mu_{i}^{t}=(1-\alpha) \cdot \mu_{i}^{t-1}+\alpha \cdot\left(X_{\text {wor }}^{t}+X_{\text {wor }}^{t}-X_{\text {wor }}^{t}\right), \\
& \sigma_{i}^{t}=(1-\alpha) \sigma_{i}^{t-1}+\alpha \cdot \sqrt{\sum_{i=1}^{M}\left(X_{i}^{t}-\mu_{i}^{t}\right)^{2} / M}
\end{aligned}
$$

where $\alpha$ is learning rate parameter with $\alpha \in(0,1]$ and $X_{\text {best }}, X_{\text {best }}$ and $X_{\text {worst }}$ represent the best, the second best and the worst individual respectively.

Step4: Sampling. Create new population by sampling new individuals from the constructed probabilistic model.

Step5. Go to Step 2 until stopping criteria are met.

## C. HSOMA

Theoretically, all individuals in the standard SOMA fly towards the optimal individual and finally converge to the best individual. So it can be imagined that other individuals will move closer to the best individual quickly if there is stagnation the best individual, which causes the population diversity decrease and leads to premature convergence finally ${ }^{[9]}$. In addition, the standard SOMA uses only the local information of individuals and has no mechanism to directly use the global information of population.

Aiming at above problems, we incorporate the EDA mechanism into the migration loop of SOMA in order to create new individuals to explore the search space more effectively. The genes of individuals in HSOMA partially come from SOMA algorithm and partially come from PBILc algorithm. The proportion of the use of two algorithms is decided by a control parameter Ps. At generation k , the new proposed hybrid migration scheme of an individual works as follows:
for $j=1$ to $D$ do
if $r n d_{j}<P_{t}$, then

$$
X_{i, j}^{M L+1}=X_{i, j, \text { start }}^{M L}+\left(X_{L, j}^{M L}-X_{i, j, \text { start }}^{M L}\right) * t * \text { PRTVector }_{j}
$$

else

$$
X_{i, j}^{M L+1}=r n d_{j} \cdot \sigma_{j}^{M L}+\mu_{j}^{M L}
$$

end if
end for
where $P_{t}$ is a uniform random number in $[0,1]$, which control the influence of two algorithms and the recommended values are from range of 0.8 to 1.0 .

The core idea of the new proposed hybrid migration scheme is based on two considerations. On the one hand, the local information of the best individuals can be used by SOMA sufficiently. On the other hand, EDA has the ability to utilize the global statistical information collected from the previous search and explore the new search space. From the analysis, the new proposed hybrid migration scheme introduces a new migration mode into SOMA, so it can increase the diversity of the population and avoid the premature convergence of SOMA.

We incorporate the new proposed hybrid migration scheme into the DE algorithm. The HSOMA is given as follows:

Step1: Define the HSOMA parameters before execution, such as Step, PathLength, PRT, $\alpha$ and $P_{t}$.

Step2: Generate the initial population within the search space.

Step3: Evaluate the fitness of the population and Find leader (the individual with the best fitness) of the population. Calculate the mean and the standard deviation according to (4).

Step4: Apart from the leader, all individuals are migrated using the new proposed hybrid migration scheme.

Step5. If the stopping criterion is satisfied, stop. Otherwise, return to Step 3.

## III. EXPERIMENTAL RESULTS AND ANALYSIS

## A. Benchmark Functions and Parameter settings

we considered five Benchmark functions used in [8] and given in Table I. Functions $\mathrm{f} 1-\mathrm{f} 2$ are unimodal. Functions $\mathrm{f} 3-\mathrm{f} 5$ are multimodal.

To demonstrate the superiority of HSOMA, three other methods, SOMA, PBILc and Hybrid Migrating Behavior Based Self-Organizing Migrating Algorithm(HBSOMA),
have been considered. All the compared algorithms adopt the same population size is 50 and the maximum number of function evaluations is 1 e 6 as a termination criterion. For all the experiments reported in this paper the SOMA, HBSOMA and HSOMA run with the common parameters for $P R T=0.10, \operatorname{PathLength}=2.1$ and Step $=0.21$. $\alpha$ is set to 0.01 and $M$ to $N / 2$ in HSOMA and PBILc. For the HBSOMA, $C R$ is random number in $[0,1] . P s$ is set to 0.95 for HSOMA.

TABLE I. Test Functions

| Name | Formulation | Dimension | Bounds | Theoretical <br> nptima/f(x*) |
| :-- | :-- | :-- | :-- | :-- |
| Sphere | $f_{1}(x)=\sum_{i=1}^{n} x_{i}^{2}$ | 30 | $[-5.12,5.12]$ | 0 |
| Quartic | $f_{2}(x)=\sum_{i=1}^{n} i * x_{i}^{4}+$ random $[0,1)$ | 30 | $[-1.28,1.28]$ | 0 |
| Rastrigin | $f_{3}(x)=\sum_{i=1}^{n}\left[x_{i}^{2}-10 \cos \left(2 \pi x_{i}\right)+10\right]$ | 30 | $[-5.12,5.12]$ | 0 |
| Ackley | $f_{4}(X)=20+e-20 e^{-\frac{1}{2}\left(x \sum_{i=1}^{n} x_{i}^{2}-e^{-\frac{1}{n}} \sum_{i=1}^{n} \cos \left(2 \pi x_{i}\right)\right.}$ | 30 | $[-32,32]$ | 0 |
| Griewank | $f_{5}(x)=\frac{1}{4000} \sum_{i=1}^{n} x_{i}^{2}-\prod_{i=1}^{n} \cos \left(\frac{x_{i}}{\sqrt{i}}\right)+1$ | 30 | $[-600,600]$ | 0 |

## B. Experimental Results and Analysis

In order to make a fair comparison, we perform 20 independent runs on each problem for these algorithms to be compared within given objective function evaluations. Table II shows the final results, where -Min", -Mean" and -Worst" stand for the best, the mean and the worst values
of optimal solutions achieved in 20 independent runs, respectively. -Std" represents the standard deviation of the obtained optimal solutions. -Eval" represents the mean number of fitness evaluations to reach the precision $1 \mathrm{e}-30$ of the 20 independent runs. The best results are highlighted in bold font.

TABLE II. STATISTIC RESULTS OF SOMA, HBSOMA, PBILC AND HSOMA.

| Function | Algorithm | Min | Mean | Max | Std | Eval |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| Sphere | SOMA | 2.442e-08 | 8.705e-06 | 7.933e-05 | 1.810e-05 | - |
|  | HBSOMA | 2.442e-08 | 2.616e-06 | 1.292e-05 | 3.694e-06 | - |
|  | PBILc | 9.358e-22 | 1.099e-21 | 1.316e-21 | 1.150e-22 | - |
|  | HSOMA | 3.227e-63 | 3.838e-62 | 1.016e-61 | 4.022e-62 | 500830 |
| Quartic | SOMA | 2.442e-08 | 1.932e-05 | 6.858e-05 | 2.113e-05 | - |
|  | HBSOMA | 2.442e-08 | 7.523e-06 | 4.402e-05 | 1.286e-05 | - |
|  | PBILc | 1.145e-20 | 1.312e-20 | 1.514e-20 | 9.777e-22 | - |
|  | HSOMA | 3.460e-62 | 3.037e-61 | 1.750e-60 | 5.149e-61 | 515040 |
| Rastrigin | SOMA | 5.951e-03 | 2.83968 | 6.14140 | 1.85656 | - |
|  | HBSOMA | 0.110745 | 2.1994 | 4.49061 | 1.24906 | - |
|  | PBILc | 0 | 0.19899 | 0.99496 | 0.41951 | 599800 |
|  | HSOMA | 0 | 0 | 0 | 0 | 404790 |
| Ackley | SOMA | 7.149e-04 | 0.010165 | 0.03744 | 0.010248 | - |
|  | HBSOMA | 7.149e-04 | 3.973e-03 | 0.01534 | 4.302e-03 | - |
|  | PBILc | 1.472e-10 | 1.751e-10 | 1.932e-10 | 1.594e-11 | - |
|  | HSOMA | 6.517e-15 | 9.359e-15 | 1.107e-14 | 1.498e-15 | - |
| Griewank | SOMA | 8.208e-03 | 0.030289 | 0.071943 | 0.020426 | - |
|  | HBSOMA | 1.677e-03 | 0.053608 | 0.24924 | 0.072232 | - |
|  | PBILc | 0 | 0 | 0 | 0 | 887150 |
|  | HSOMA | 0 | 0 | 0 | 0 | 415080 |

From Table II, it can clearly be seen that HSOMA has HSOMA achieves significant improvements on the five the better -Min", -Mean", -Worst", -Std" and -Eval" the better -Min", -Mean", -Worst", -Std" and -Eval" results than those obtained by SOMA, HBSOMA, PBILc on functions $\mathrm{f} 1, \mathrm{f} 2, \mathrm{f} 3$ and f 4 . The results obtained by HSOMA is similar to PBILc on function f 5 and obviously superior to the other two algorithms, but the mean number of fitness evaluations to reach the precision $1 \mathrm{e}-30$ needed by HSOMA is smaller than that of PBILc. Thus, by combining SOMA with PBILc in gene hybrid model,

![img-0.jpeg](img-0.jpeg)

Figure 1. The averaged convergence curve of $f 1$
![img-1.jpeg](img-1.jpeg)

Figure 2. The averaged convergence curve of $f 2$
![img-2.jpeg](img-2.jpeg)

Figure 3. The averaged convergence curve of $f 4$
![img-3.jpeg](img-3.jpeg)

Figure 4. The averaged convergence curve of $f 5$
From Fig.1-4, it can be seen that the convergence curves of SOMA and HBSOMA descend faster than HSOMA at the early stage of the evolution. But at the middle and the last stages of the evolution, HSOMA
achieves a faster convergence than that of the other algorithms. PBILc algorithm converges at the slowest speed in the early stage of the evolution, but it can escape from local optima. So, it is concluded that HSOMA is more efficient and effective than SOMA, HBSOMA and PBILc on these problems.

In general, the overall performance of HSOMA is better than other three algorithms within given fitness evaluations for the tested problems.

## IV. CONCLUSIONS

In this paper, we have proposed an improved SOMA based on the estimation of distribution algorithm, called HSOMA. HSOMA combines SOMA and EDA in gene hybrid model to overcome the problem of premature convergence and keep the diversity of population, which incorporates local information of best individual and global information of population together.

HSOMA is tested on five benchmark problems and compared with SOMA, PBILc and HBSOMA. The experimental results demonstrated that for the test problems, HSOMA exhibits higher convergence velocity, and more robustness than the SOMA, PBILc and HBSOMA. In the future, we intend to refine HSOMA and apply it to solve engineering optimization problems.

## ACKNOWLEDGMENT

This work is supported by Foundation for Distinguished Young Talents in Higher Education of Guangdong China(No. 2012LYM 0054) and Guangzhou Planning Project of Science and Technology(No. 2013Y200043).

## REFERENCES

[1] I. ZELINKA, J. LAMPINEN, -SOMA-Self-Organizing Migrating Algorithm, " Proceedings of the 6th International Conference on Soft Computing (Mendel 2000), Brno, Czech Republic, JUN. 2000, pp 177-187.
[2] L. D. S. Coelho, -Self-organizing migrating strategies applied to reliability-redundancy optimization of systems," IEEE Transactions on Reliability, Volume 58, Issue 3, September 2009, pp. 501-510, doi:10.1109/TR.2009.2019514.
[3] T. HORÁK, N. ASTORAKIS, and M. LÁNSKÁ, Report on Recent Scientific Applications of Self-Organizing Migration Algorithm," Proceedings of the 12th WSEAS International Conference on Applied Informatics and Communications (AIC'12), Istanbul, Turkey, Czech Republic, August 2012, pp. 247-251.
[4] P.Kadlec, Z. RAIDA, and J. DĔÍNOVSKÝ, -Multi-Objective SelfOrganizing Migrating Algorithm: Sensitivity on Controlling Parameters," Radioengineering, Volume 22, Issue 1, April 2013, pp. 296-308.
[5] D. Davendra, I. Zelinka, M. Bialic-Davendra, R. Senkerik, and R. Jasek, -Discrete Self-Organising Migrating Algorithm for flowshop scheduling with no-wait makespan, " Volume 57, Issues 1-2, January 2013, pp. 100-110, doi:10.1016/j.mcm.2011.05.029.
[6] LIN Zhi-yi and WANG Ling-ling, -Opposition-based SelfOrganising Migrating Algorithm," Computer Science, Volume 39, Issue 5, May 2012, pp. 217-218, 233.
[7] D. Singh and S. Agrawal, -A Novel Hybrid Self Organizing Migrating Algorithm with Mutation for Global Optimization," International Journal of Soft Computing and Engineering, , Volume 3, Issue 6, January 2014, pp. 101-106.
[8] LIN Zhi-yi, LI Yuan-xiang and WANG Ling-ling. -Hybrid Migrating Behavior Based Self-Organising Migrating Algorithm," Volume 35, Issue 12, December 2008, pp. 175-177. 175-177.

[9] L. D. S. Coelho and V. C. Mariani, -An efficient cultural selforganizing migrating strategy for economic dispatch optimization with valve-point effect," Energy Conversion and Management, Volume 51, Issue 12, December 2010. pp. 2580-2587, doi: 10.1016/j.enconman.2010.05.022.
[10] M. Hauschild and M. Pelikan, -An introduction and survey of estimation of distribution algorithms," Swarm and Evolutionary

Computation, Volume 1, September 2011 pp .111-128, doi: 10.1016/j.swevo.2011.08.003.
[11] M .SEBAG \& DUCOULOMBIER. A. Extending population-based incremental learning to continuous search spaces. Parallel Problem Solving from Nature-PPSN V. Springer Berlin Heidelberg, January 1998, pp. 418-427, doi: 10.1007/BFb0056884.