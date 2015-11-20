### Introduction

In this assignment, we learn about writing R functions that are able to 
cache potentially time-consuming computations. For example, taking the mean 
of a numeric vector is typically a fast operation. However, for a very long 
vector, it may take too long to compute the mean, especially if it has to be 
computed repeatedly (e.g. in a loop). If the contents of a vector are not 
changing, it may make sense to cache the value of the mean so that when we need 
it again, it can be looked up in the cache rather than recomputed. Here, we will take 
advantage of R's scoping rules and how they can be manipulated to preserve state 
inside of an R object. The `<<-` operator can be used to
assign a value to an object in an environment that is different from the
current environment.

### Caching the Inverse of a Matrix

Matrix inversion is usually a costly computation and there may be some
benefit to caching the inverse of a matrix rather than computing it
repeatedly (there are also alternatives to matrix inversion that we will
not discuss here). Here we write the following functions:

1.  `makeCacheMatrix`: creates a special "matrix" object
    that can cache its inverse.
2.  `cacheSolve`: computes the inverse of the special
    "matrix" returned by `makeCacheMatrix` above. If the inverse has
    already been calculated (and the matrix has not changed), then
    `cacheSolve` should retrieve the inverse from the cache.

Computing the inverse of a square matrix can be done with the `solve`
function in R. For example, if `X` is a square invertible matrix, then
`solve(X)` returns its inverse.

We assume that the matrix supplied is always
invertible.

