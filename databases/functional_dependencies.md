# Functional Dependencies




Decomposition: used to find the BCNF relations which are function dependencies that are keys (keys are FD that allow you to reach all the attributes)

1. Closure on the right side of all FD
2. If closure is not a key then it violates the BCNF and must be decomposed
3. Decompose
    * separate into branches based on left side of one of the closures, other branch is remainder + initial closure
    * find closure of new attributes
    * eliminate attributes until left with new FD
    * check if BCNF
    * continue with non BCNF

Build the tables based on the decomposed relations