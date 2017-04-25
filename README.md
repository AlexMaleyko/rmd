# rmd
### Artificial Bee Algorithm
Pseudocode:
```
BEGIN
Initialize the solution population xm, 1 = l, ..., SN
Evaluate popoulation
cycle = 1
REPEAT
Generate new solutions for the employed bees using (ii) and evaluate them.
Keep the best solution between current and candidate
Select the visited solution for onlooker bees bu their fitness
Generate new solutions for the onlooker bees using (ii) and evaluate them
Keep the best solution between current and candidate
Determine if exist an abandoned food source and replace it using a cout bee
Save in memory the best solution so far
cycle = cycle + 1
UNTIL cycle = M C N
```
### Grey Wolf Optimization
Pseudocode:
```
BEGIN
  Initialize the grey wolf population Xi (i = 1, 2, ..., n)
  Initialize a, A, and C
  Calculate the fitness of each search agent
  WHILE count < max number of iterations
    FOR each search agent
      Update te position of the current search agent
    END FOR
    Update a, A, and C
    Calculate the fitness of all search agents
    Update the best search agent, the 2nd best serach agent, and the 3rd best search agent
    ADD 1 to count
  END WHILE
  RETURN the best search agent
END
```
### Bat Algorithm
Pseudocode:
```
BEGIN
  Objective function f(x), x=(x1, ...,xd)^T
  Initialize the bat population x_i (i= 1, 2, ..., n) and v_i
  Define pulse frequency f_i at x_i
  Initialize pulse rates r_i and the loudness A_i
  WHILE count < max number of iterations
    Generate new solutions by adjusting frequency, and updating velocities and locations/solutions
    IF rand > r_i
      Select a solution among the best solutions 
      Generate a local solution around the selected best solution
    END IF
    Generate a new solution by flying randomly
    IF rand < A_i AND f(x_i) < f(x_*)
      Accept the new solutions
      Increase r_i and reduce A_i
    END IF
  Rank the bats and find the current best x_*
  END WHILE
  Postprocess results and visualization
  ```
  ###Firefly Algorithm
  Pseudocode:
  ```
  Objective function f(x), x=(x_1, x_2, ... , x_d)^T
  Initialize a population of fireflies x_i(i = 1,2, ..., n)
  Define light absorption coefficient gamma
  WHILE count < MaximumGeneratons
    FOR i = 1:n (all n fireflies)
      FOR j = 1:i
        Light intensity Ii at x_i is determined by f(xi)
        IF I_i > I_j
          Move firefly i towards j in all d dimensions
        ELSE
          Move firefly i randomly
        END IF
      Attractiveness changes with distance r via exp[0gamma r2]
      Determine new solutions and revise light intensity
      END FOR j
    END FOR i
    Rank the fireflies according to light intensity and find the current best
  END WHILE
  ```
  ### Cuckoo Search Optimization
  Pseudocode:
  ```
  BEGIN
    Generate start population of n nests x_j, (j = 1, 2, ... ,n)
    REPEAT
      Place cuckoo to point x_i randomly by performing Levy flights
      Choose nest j among n nests randomly
      IF F_i < F_j
        Replace x_j on new solution
      END IF
      Delete from the population nests found with pa probability and build the same number of new nests
      SAVE best solution (nest)
    UNTIL stop criteria
    Postprocess results and visualization
    ```
 ### Bacteria Foraging Optimization
 Pseudocode:
 ```
 
  
