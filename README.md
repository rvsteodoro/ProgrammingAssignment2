## Two functions (makeCacheMatrix and cachesolve) will
## cache the inverse of the given matrix

## makeCacheMatrix : It creates a matrix that will be able to
## cache its inverse
makeCacheMatrix <- function(x = matrix()) {

  ## Provides the inverse property
  i <- NULL
  
  ## STEP 1 : Set the value of the matrix
  set <- function(y) {
    x <<- y
    i <<- NULL  
}

  ## STEP 2 : Get the value of the matrix
  get <- function() x
        
  ## STEP 3 : Set the values of the inverse matrix
  setInverse <- function(inverse) i <<- inverse
        
  ## STEP 4 : Get the value of the inverse matrix
  getInverse <-function() i
        
  ## Generate a list for the function
  list(set = set,
       get = get,
       setInverse = setInverse,
       getInverse = getInverse)
}
        
## cacheSolve : Calculates the inverse of the cache matrix
## that was generated by the first function
cacheSolve <- function(x, ...) {
        
  ## Return a matrix that is the inverse of 'x'
  i <- x$getInverse()
  if (!is.null(i)) {
    message("Processing...")
    return(i)
  }
        
  ## Get the matrix from the object
  m <- x$get()
        
  ## Generate the inverse matrix
  i <- solve(m, ...)
  x$setInverse(i)
  i
}
