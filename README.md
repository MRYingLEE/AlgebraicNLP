To use NLP machine learning model along with Algebra to solve symbolic mathematics problems in a more general and smarter way, compared to and inspired by the project facebookresearch/SymbolicMathematics (https://github.com/facebookresearch/SymbolicMathematics). 

# AlgebraicNLP
When Algera meets NLP, NLP can be used to solve algebra problems, algebra can be used to solve NLP problem at the same time.

## What can Algebra bring to NLP?
Algebra can be used to describe semi-structured relation. Structured data, such as image, time series, can be described easily. None structured data, such as natural language, can be processed by NLP. 
Semi-structured data is hard to describe and process.

### Syntax tree can be used to describe the semi-structured data.
Structured NLP ( Syntax Tree, RegEX, Symbolic Math)
Directional offered operation, unordered

### Syntax tree can be treated as a tree of syntax tree.
So that the learning can be symplified.

For example, The integral of f(x)+g(x) = the integral of f(x) + the integral of g(x).

### Parameters can make the syntax tree more general.
So that NLP can deal with all specific values with one template. At the same time, the training size is shrinked greatly. In other words, there are much less for the model to memorize.

(At the same time, there is a corresponding model problem. All the parameters are positional to the other parts, but the order of parameters in the parameters are meaningless. for example, ax+b has the same structure as bx+a. All permutation possibilities for the parameters can be used to train the model, but I still has no idea to model this feature efficiently.)

### Prefix or postfix can turn the syntax tree into a sequence.
So that normal sequence based NLP models can be used.

## What can NLP bring to Algebra?
### NLP can make Algera more experience based.
### NLP can be fast
Use NLP to solve Math.

## In short, Algera makes NLP more clever, from Arithmetic to Algebra.

# An experiment is to solve a Symbolic Math problem, Integral specifically.
I am working on it in my spare time and hope I can finish it in 1 or 2 month.

## What I have learnt?

### The dataset generation is very tough and slow

We are using Sympy (https://www.sympy.org) to generate a dataset for training and testing. 

Due to the limits of Sympy, some expressions cannot be integrated in a specific time (such as 1 minute). We have to use timeout to limit the transform process.
The generating is slow and is CPU bound. So that multiprocessing, a process-based parallelism, should be used to speed at the times of your CPU cores. In order to use multiprocessing, splitting the original dataset, which has more than 45m rows, is needed at first.

### The training for a new model is very slow
To train a new model for the specific symbolic mathematical problem (Integral indeed) is very slow. I used to take one week to train the model from scratch and only got a 70% accuracy, which is not acceptable. 
The original paper actually mentioned a lot of calculation resources had been used.
It is not practical for me to train a totally model.

More experimental detail can be found at the Data generation Experiment.ipynb. 

### Conclusion: 
I used to make a conclusion as to use Derivative instead of Integral. Due to the very slow training. I have to change my mind again and back to the original idea, which is to solve the integral problem.

In order to speed the training and to compare the algebraic method with the arithmetic one, transfer learning should be used to speed the training.



