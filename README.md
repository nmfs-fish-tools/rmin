
## minimizR

minimizR is a l-bfgs function minimizer that works with freely estimable or box constrained parameter sets. 

## Freely Estimated Example

Here is an example of minimizing the Rosenbrock function.

```{r min}
library(minimizR)

#Rosenbrock function
objective <- function(x) {
  return( 100 * (x[2] - x[1] * x[1])^2 + (1 - x[1])^2 )
}

#Rosenbrock gradient function
gradient <- function(x) {
  return( c( -400 * x[1] * (x[2] - x[1] * x[1]) - 2 * (1 - x[1]), 200 * (x[2] - x[1] * x[1]) ) )
}

#estimated parameters
x<-c(-1.2, 0)

#minimizR function
opt<-minimizR(x,                   #initial parameters values
             objective,            #objective function
             gradient,             #gradient function
             control = list(       #control list
             tolerance = 1e-4,     #convergence criteria
             verbose = TRUE,       #print status
             iprint = 10))         #print interval

```

## Output
```{r out}
print(opt)
```

## Value Bounded Example

Here is an example of minimizing the Rosenbrock function. Note, this example uses value bounded parameters. If "lb" and "ub" are omitted from the control list, all parameters will be freely estimated.  

```{r minb}
library(minimizR)

#Rosenbrock function
objective <- function(x) {
  return( 100 * (x[2] - x[1] * x[1])^2 + (1 - x[1])^2 )
}

#Rosenbrock gradient function
gradient <- function(x) {
  return( c( -400 * x[1] * (x[2] - x[1] * x[1]) - 2 * (1 - x[1]), 200 * (x[2] - x[1] * x[1]) ) )
}

#estimated parameters
x<-c(-1.2, 0)

#minimizR function
opt<-minimizR(x,                    #initial parameters values
              objective,            #objective function
              gradient,             #gradient function
              control = list(       #control list
              tolerance = 1e-4,     #convergence criteria
              lb = c(-1.5, -1.5),   #lower bounds
              ub = c(1.5,1.5),      #upper bounds
              verbose = TRUE,       #print status
              iprint = 10))         #print interval

```

## Output
```{r outb}
print(opt)
```

