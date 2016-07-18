#A Few Useful Things to Know about Machine Learning
## Learning = Representation + Evaluation + Optimization
  * 对应李航《统计学习方法》中的模型+策略+算法
  * Representation
    * Instances
      * K-nearest neighbor
      * SVM
    * Hyperplanes
      * Naive Bayes
      * Logistic Regression
    * Decision Trees
    * Sets of Rules
      * Propositional rules
      * Logic Programs
    * Neural networks
    * Graphical models
      * Bayesian networks
      * Conditional random fields
  * Evaluation
    * Accuracy/Error rate
    * Precision and Recal and F1-score
    * Squared error
    * Likelihood
    * Posterior probability (not understand)
    * Information Gain
    * K-L divergence (not understand)
    * Cost/Utility
    * Margin
  * Optimization
    * Combinatorial optimization
      * Greedy search
      * Beam search
      * Branch-and-bound
    * Continuous optimization
      * Unconstrained
        * Gradient descent
        * Conjugate gradient (not)
        * Quasi-Newton method (not)
      * Constrained
        * Linear programming
        * Quadratic programming
        
## It's genralization that counts
  * 泛化能力
  * Fundamental goal of machine learning: to generalize beyond the examples in the training set.
  * Don't have access to function we want to optimize!
  * Training error as a surrogate for test error.
  
## Data alone is not enough
  * Every learner must embody some knowledge or assumptions beyond the data 
    it's given in order to generalize beyond it.
  * General assumptions are enough to do very well.
    * smoothness
    * similar examples having similar classed
    * limited dependences 
    * limited complexity
  * Key criteria for choosing representation
    * which kinds of knowledge are easily expressed in it
    
## Overfitting has many faces
  * Bias: a learner's tendency to consistently learn the same wrong thing
  * Variance: tendency to learn random things irrespective of the real signal
  * Combat methods
    * Cross-validation
    * Regularization
    * Statistical significance test like chi-squre (not)
  * Overfitting is not caused by noise
  * Multiple testing (not?)
## Intuition fails in high dimensions
  * Curse of dimensionality
  * Similarity-based reasoning ml depend on breaks down in high dimensions
  * In high dimensions all examples look alike (??)
  * Counter intuitive in high dimension
    * most of the mass of a multivariate Gaussian distribution not near mean, but
      in an increasingly distant shell around it (??)
    * most of the volume of a high-dimensional orange is in the skin, not the pulp.
    * arrroximate a hypersphere by inscribing it in a hypercule, in high dimensions
      almost all the volume of the hypercube is outside the hypersphere.
      bad news for ml, where shapes of one type are often approximated by shapes of another(??)
  * Blessing of non-uniformity

## THeoretical guarantees are not what they seem
  * not really understand (??)

## Feature engineering is the key
  * ML is not a one-shot process of buiding a data set and running a learner, but rather an iterative process of
    * running the learner
    * analyzing the results
    * modifying the data and/or the learner
    * repeating
  
## More data beats a cleverer algorithm
  * All learners essentially work by grouping nearby examples into the same class
  * The key difference is in the meaning of "nearby"
  * Pays to try the simplest learners first
    * naive Bayes
    * Logistic Regression
    * K-nearest neighbor
    * SVM
  * ML projects often wind up having a significant component of learner design, and practitioners need to have
    some expertise in it.
    * Article: Machine learning as experimental science

## Learn many models, not just one
  * model ensembles
  * not confused with Bayesian model averaging

## Simplicity does not imply accuracy
  * SVM can be very complex

## Representable does not imply learnable
## Correlation does not imply causation
## My Getaway
  * I should know what is statistical test
