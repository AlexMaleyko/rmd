# rmd
### Artificial Bee Algorithm
current best
Pseudocode:
```
BEGIN

Initialize the population
Find current best agent for the initial iteration
SET global best to current best
IF n <= 10
  a = n - n%2
  b = 1
  c = 1
  d = 1
ELSE
  a = n%10
  b = 5
  c = (n - a*b - a)%2
  d = 2
END IF
FOR iterator = 0:iteration
  evaluate fitness for each agent
  sort fitness in ascending order and get best agents
  from best agents list select agents from a to c
  newbee?
  self.scout=?
  self_point=?
  Evaluate current best agent
  IF function(current best) < function (global best)
    global best = current best
  END IF
END FOR
Save global best
```
### Grey Wolf Optimization
Pseudocode:
```
BEGIN
  Initialize randomly the grey wolf population
  Find 1st, 2nd and 3rd best agents (alfa, beta, delta)
  Set global best agent to the 1st best agent
  Calculate the fitness of each search agent
  WHILE count < max number of iterations
    FOR each search agent
      Update te position of the current search agent
    END FOR
    Update alfa, beta and gamma
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
  ### Firefly Algorithm
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
  END
  ```
  ### Whale Swarm lblgorithm
 Pseudocode:
 ```
 BEGIN
  Initialize agents
  Find current best
  global best = current best
  FOR t = 0:number of iterations
    FOR each agent
      find better and nearest
      IF  Exists
        move current agent in direction of its better and nearest
      END IF
      find current best
      IF current best better than global best
        SET global best to current best
      END IF
    END FOR
   Save golobal best
 END
 ```
 ### Firework Algorithm
 Pseudocode:
 ```
 BEGIN
  Initialize agents
  Find current best
  global best = current best
  
  FOR i= 0:nuber of agents
    evaluate function value for current best and worst
    FOR each agent
      perform explosion
      perform gausian mutation
   END FOR
   apply mapping rule
   Select new agents according to the selection strategy
   IF current best better than global best
        SET global best to current best
   END IF
   END FOR
  save global best
END
```
 
 ### Bacteria Foraging Optimization
 Pseudocode:
 ```
BEGIN
Initialize randomly the bacteria foraging optimization population
  Calculate the fitness of each agent
  Set global best agent to best agent
  FOR number of iterations	
    FOR number of reproduction steps
      FOR number of chemotactic steps	
        FOR each search agent
          Move agent to the random direction
          Calculate the fitness of the moved agent
          FOR swimming length
            IF current fitness is better than previous
              Move agent to the same direction
            ELSE
              Move agent to the random direction
            END IF
          END FOR				
        END FOR
        Calculate the fitness of each agent
      END FOR	
      Compute and sort sum of fitness function of all chemotactic loops (health of agent)
      Let live and split only half of the population according to their health
    END FOR
    Update the best search agent
    IF not the last iteration
      FOR each search agent
        With some probability replace agent with new random generated
      END FOR
    END IF	
    Calculate the fitness of each agent
  END FOR
END
```

### Particle swarm optimization
Pseudocode:
```
BEGIN
  Initialize agents
  Find current best
  Set global best = current best
  FOR i= 0 : number of iterations
    Calculate particle velocity
    Chage particles velocity
    Update particles positions
    Select new agents according to the selection strategy
    IF current best better than global best
      SET global best to current best
    END IF
  END FOR
  save global best
END
```
### Chicken Swarm Optimization
Pseudocode:
```
BEGIN
  Initialize a population of N chickens and define the related parameters
  Evaluate the N chickens' fitness values
  Find current best
  Set global best = current best
  FOR t = 0 : number of iterations
    IF(t % G == 0)
      Rank the chickens' fintess values and establish a hierarchal order in the swarm
      Divide the swarm into different groups, and determine the relationship 
      between the chicks and mother hens in a goup
    END IF
    FOR i = 1 : N
      IF i == rooster
        Update its solution and location using equation for roosters
      END IF
      IF i == hen
        Update its solution and location using equation for hens
      END IF
      IF i == chick
        Update its solution and location using equation for chicks
      END IF
      Evaluate current best
      IF current best better than global best
        SET global best to current best
      END IF
  END FOR
END
```
### Social Spider Algorightm
Pseudocode:
```
BEGIN
  Create the population of spiders
  Initialize target vibration for each spider
  FOR i = 0 : number of iterations
    FOR each spider in population
      Evaluate the fitness values of a spider
      Generate a vibration at the position of the spider
    END FOR
    FOR each spider in population
      Calculate the intensity of the vibrations generated bu other spiders
      Select the strongest vibration from all vibrations
      IF the intensit of the strongest vibration is larger than target vibration
        target vibration = strongest vibration
      END IF
      Perform a random walk towards target vibration
      Generate a random number rn from [0,1)
      IF rn < p_j
        Assign a random position to the spider
      END IF
      Attenuate the intensity of target vibration
    END FOR
  END FOR
  Save the best solution
END
END
