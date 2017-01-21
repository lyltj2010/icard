### Hessian Matrix

Hessian is a square matrix of second-order partial derivatives of a scalar-valued function. It describes the local curvature of a function of many variables.   

Suppose $f:R^n \rightarrow R$, if all second partial derivatives of $f$ exist and are continuous over the domain of the function, then the Hessian matrix $H$ of $f$ is a square $n \times n$ matrix.

![Hessian](./img/hessian.svg)

### Second Derivative Test

Test if a critical point $x$ is a local maximum, local minimum, or a [saddle point](https://en.wikipedia.org/wiki/Saddle_point).  

- If $H$ is **positive definite**, then $f$ attains an isolated local minimum at $x$
- If $H$ is **negative definite**, then $f$ attains an isolated local maximum at $x$
- If $H$ has both positive and negative eigenvalues, then $x$ is a saddle point for $f$
- Otherwise the test is inconclusive

### References

- [Hessian matrix - Wikipedia](https://en.wikipedia.org/wiki/Hessian_matrix)