
# rmd

### Gray Wolf Optimization
#### Description
The **Gray Wolf Optimization algorithm** mimics the leadership hierarchy and
hunting mechanism of gray wolves in nature. Wolves live in a pack. 
The average pack consists of a family of 5–12 animals.
wolves have strict social hierarchy which is represented by the division of a pack into four
levels: alpha, beta, delta, and omega.<br>
_Alpha_ wolves are the leaders of their pack. They are responsible for making decisions, but sometimes 
alphas can obey to other wolfes of the pack.<br>
_Beta_ wolves help alphas make decisions, every beta is a candidate 
to become an alpha if an alpha has died or aged.
A beta respects an alpha and transfers commands to the pack, ensures discipline among inferior wolves 
and provides a feedback from the pack to an alpha.<br>
_Delta_ wolves have to submit to alphas and betas, but they dominate the omega.<br>
Finally, _omega_ wolves have to obey all other wolves. Sometimes they play a role of caretakers.<br><br>
Gray wolf hunting has three main phases:
* Tracking, chasing, and approaching the prey
* Pursuing, encircling, and harassing the prey until it stops moving
* Attack towards the prey
#### Mathematical model
In mathematical model of the social hierarchy 
of wolves is mapped to the solution fit. The fittest 
solution is considered to be the alpha. Beta and delta are the second and
third best solutions respectively.
The rest of the candidate solutions are assumed to be omega.<br>
Alpha, beta and delta lead the hunting (optimization) and omega wolves follow these three wolves.
#### Algorithm
<pre>
BEGIN
&nbsp;&nbsp;Initialize randomly the gray wolf population
&nbsp;&nbsp;Find 1st, 2nd and 3rd best agents (&alpha;, &beta;, &delta;)
&nbsp;&nbsp;Set global best agent to the 1st best agent
&nbsp;&nbsp;Calculate the fitness of each search agent
&nbsp;&nbsp;WHILE count &lt; max number of iterations
&nbsp;&nbsp;&nbsp;&nbsp;FOR each search agent
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Update te position of the current search agent
&nbsp;&nbsp;&nbsp;&nbsp;END FOR
&nbsp;&nbsp;&nbsp;&nbsp;Update &alpha;, &beta; and &delta;
&nbsp;&nbsp;&nbsp;&nbsp;Calculate the fitness of all search agents
&nbsp;&nbsp;&nbsp;&nbsp;Update the best search agent, the 2nd best serach agent, and the 3rd best search agent
&nbsp;&nbsp;&nbsp;&nbsp;ADD 1 to count
&nbsp;&nbsp;END WHILE
&nbsp;&nbsp;RETURN the best search agent
END
</pre>
#### Arguments
The gwo method accepts the following arguments:<br>
**n**: number of agents<br>
**function**: test function<br>
**lb**: lower limits for plot axes<br>
**ub**: upper limits for plot axes<br>
**dimension**: space dimension<br>
**iteration**: number of iterations
#### Method invocation
The method can be invoked by passing the arguments in the following order:
```
SwarmPackagePy.pso(n, function, lb, ub, dimension, iteration)
```
### Bat Algorithm
#### Description
The **Bat Algorithm** is based on the bats echolocation ability. By using echolocation bats can detect
their food and preys and even distinguish between the different kinds of insects in the darkness.
A bat emits a loud sound and listens to the echo which is created from the sound reflection from the surrounding objects.
Sounds emmited by a bat are vary in properties and can be used depending on the hunting strategy.<br>
Each sound impulse lasts from 8 to 10 milliseconds and has constant frequency between 25 and 150 KHz.
A bat can emit from 10 to 20 of supersonic impulses per second, an impulse lasts from 5 to 20 milliseconds.
The number of signals emited by a bat can be increased during a hunt to 200.
#### Mathematical model
The Bat Algorithm uses the following principles:
1. A bat uses echolocation for distance estimation and "knows" the difference between the food/prey and an obstacle
2. Bats fly randomly with a velocity of &nu;<sub>i</sub> in the position x<sub>i</sub>, fixed frequency f<sub>min</sub>, variable wavelength &lambda;  and loudness A<sub>0</sub> for the search of a prey. They can automatically adjust the wave length (or frequency) of emitted sound impulse and level of emission r &isin; [0, 1] depending on the proximity to the victim.
3. While the loudness can be changed by different means we assume that the loudness vary from big positive value A<sub>0</sub> to minimum constant A<sub>min</sub>.
In addition to these simplified principles, lets use the next approximations: frequency f from the segment [f<sub>min</sub>, f<sub>max</sub>] corresponds to the wavelength segment [&lambda;<sub>min</sub>, &lambda;<sub>max</sub>]. For instance, a frequency segment [20 KHz, 500 KHz] corresponds to wavelength segment [0.7 mm, 17 mm].<br>
For this tast any wave length can be used. Moreover, it is unnecessary to use wave lengths, instead we can change the frequency and leave the wave length to be constant.
#### Algorithm
<pre>
BEGIN
Objective function f(x), x=(x<sub>1</sub>, ...,x<sub>d</sub>)<sup>T</sup>
Initialize the bat population x<sub>i</sub> (i= 1, 2, ..., n) and v<sub>i</sub>
Define pulse frequency f<sub>i</sub> at x<sub>i</sub>
Initialize pulse rates r<sub>i</sub> and the loudness A<sub>i</sub>
  WHILE count &lt; max number of iterations
    Generate new solutions by adjusting frequency, and updating velocities and locations/solutions
    IF rand &gt; r<sub>i</sub>
      Select a solution among the best solutions 
      Generate a local solution around the selected best solution
    END IF
    Generate a new solution by flying randomly
    IF rand &lt; A<sub>i</sub> AND f(x<sub>i</sub>) &lt; f(x<sub>*</sub>)
      Accept the new solutions
      Increase r<sub>i</sub> and reduce A<sub>i</sub>
    END IF
    Rank the bats and find the current best x<sub>*</sub>
  END WHILE
  Postprocess results and visualization
  </pre>
  #### Arguments
The ba method accepts the following arguments:<br>
- r0: level of impulse emission (default value is 0.9)<br>
- V0: volume of sound (default value is 0.5)<br>
- fmin: min wave frequency (default value is 0)<br>
- fmax: max wave frequency (default value is 0.02)<br>
  fmin = 0 and fmax =0.02 - the bests values<br>
- alpha: constant for change a volume of sound (default value is 0.9)<br>
- csi: constant for change a level of impulse emission (default value is 0.9)
#### Method invocation
The method can be invoked by passing the arguments in the following order:
```
SwarmPackagePy.ba(n, function, lb, ub, dimension, iteration, r0, V0, fmin, fmax, alpha, csi)
```
  ### Artificial Bee Algorithm
Pseudocode:
<pre>
BEGIN
Initialize the population
Find current best agent for the initial iteration
SET global best to current best
IF n &le; 10
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
FOR iterator = 0 : iteration
  evaluate fitness for each agent
  sort fitness in ascending order and get best agents
  from best agents list select agents from a to c
  Create new bees which will fly to the best solution
  Evaluate current best agent
  IF function(current best) &lt; function (global best)
    global best = current best
  END IF
END FOR
Save global best
</pre>
  ### Firefly Algorithm
  Pseudocode:
  <pre>
  Objective function f(x), x=(x<sub>1</sub>, x<sub>2</sub>, ... , x<sub>d</sub>)<sup>T</sup>
  Initialize a population of fireflies x<sub>i</sub>(i = 1, 2, ... , n)
  Define light absorption coefficient gamma
  WHILE count &lt; MaximumGeneratons
    FOR i = 1 : n (all n fireflies)
      FOR j = 1 : i
      Light intensity Ii at x<sub>i</sub> is determined by f(x<sub>i</sub>)
      IF I<sub>i</sub> > I<sub>j</sub>
          Move firefly i towards j in all d dimensions
        ELSE
          Move firefly i randomly
        END IF
        Attractiveness changes with distance r via exp[-&gamma; r<sub>2</sub>]
      Determine new solutions and revise light intensity
      END FOR j
    END FOR i
    Rank the fireflies according to light intensity and find the current best
  END WHILE
  </pre>
  ### Cuckoo Search Optimization
  Pseudocode:
 <pre>
  BEGIN
    Generate initial population of n nests x<sub>j</sub>, (j = 1, 2, ... ,n)
    REPEAT
      Place cuckoo to point x<sub>i</sub> randomly by performing Levy flights
      Choose nest j among n nests randomly
      IF F<sub>i</sub> &lt; F<sub>j</sub>
      Replace x<sub>j</sub> on new solution
      END IF
      Delete from the population nests found with pa probability and build the same number of new nests
      SAVE best solution (nest)
    UNTIL stop criteria
    Postprocess results and visualization
  END
  </pre>
  ### Whale Swarm lblgorithm
 Pseudocode:
 <pre>
 BEGIN
  Initialize agents
  Find current best
  global best = current best
  FOR t = 0 : number of iterations
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
 </pre>
 ### Firework Algorithm
 Pseudocode:
 <pre>
 BEGIN
  Initialize agents
  Find current best
  global best = current best
  
  FOR i= 0 : nuber of agents
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
</pre>
 
 ### Bacteria Foraging Optimization
 Pseudocode:
 <pre>
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
</pre>

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
<pre>
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
      IF rn &lt; p<sub>j</sub>
        Assign a random position to the spider
      END IF
      Attenuate the intensity of target vibration
    END FOR
  END FOR
  Save the best solution
END
</pre>
