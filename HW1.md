Due Sept 31st on D2L


#### (1) Develop a function that will take a formula `y~x1+x2,...,` and a data frame `data=..` and will, internally, produce the incidence matrix for the linear model and produce a table equal to the one
returned by `summary(lm(y~x1+x2....))`. Carry all the computations using matrix and scalar computations (you are not allowed to use `lm` or other R functions designed for least squares regression (e.e., `lsfit`).

Use the following simulation to compare your results with those of `summary(lm(y~...))`.

Your report must show:
 - The function
 - The ouput of a comparison with `lm`

```r
  n=100
  b=c(4,-4,3)
  p=length(b)
  x1=rnorm(n)
  x2=runif(n)
  x3=rbinom(n,size=1,prob=.3)
  signal=20+cbind(x1,x2,x3)%*%b
  error=rnorm(n=n,sd=sd(signal))
  y=signal+error
```

### (2) Scatter-plot smoothing

The script below simulates data using a function that is a weighted sum of sin and cosine functions plus an error term that explaines 1/3 of the variance of the response.

```r
  x=seq(from=0, to =4*pi,by=.2)
  f=function(x){ cos(x)+sin(x*2)/2}
  signal=100+f(x)
  y=signal+rnorm(sd=sqrt(var(signal)/3),n=length(x))
  
```

Fit natural splines with 3, 4, 6, 8, 12, 16, 20 and 40 degrees of freedom. Report:

 2.1. A pannel 4x2 panel of plots with each cell containing, for a model DF, a scatter plot of the simulated data, with a red line representing the real function and a blue line representing the fitted spline.
 
 2.2. A Table containgin DF, R-sq., Adj R-sq, AIC, BIC, and the MSE of estimation of the function (i.e., `mean((f(x)-predict(fm))^2)`.
 
 2.3. Which model DF would you choose?
 
 