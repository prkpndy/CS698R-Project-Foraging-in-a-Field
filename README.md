# CS698R-Project-Foraging-in-a-Field-3
<h1> Abstract </h1>
Foraging has been an essential activity for survival in the wild.  In our case, the environment contains patches of berries that are non-renewable, the agent loses reward for every movement and dies after a certain amount of time. The goal of our agent is to find an optimum foraging policy that maximizes the reward in a static environment where the resources are limited and there exists a moving cost but no cost when the agent is at rest. The agent can choose to leave the current patch of berries to explore for more patches or stop moving and conserve its rewards collected so far. This setting can be compared with the consumption of rare natural non-renewable resources, using these do generate wealth but also requires an effort to search and extract. 
As described above, our goal is to find an optimal solution for collecting berries from a field. The field has berries spread in randomly distributed patches. The agent's goal is to collect the maximum amount of juice (which will be its reward) in a given time frame by moving in 8 directions (N, NE, E, SE, S, SW, W, NW). The agent can increase the amount of juice by collecting more berries, and it will lose the juice while moving around in the field (at a constant rate). Depending on the size, there are four kinds of berries in the field. The bigger the berry, the more is the amount of juice the agent will get by collecting it (linear relation between berry size and the amount of juice it contains)

<h1> Solution Approach </h1>
The first solution proposed to solve the research problem is the Deep Q Networks. Since the problem we are trying to solve is very similar in nature to the Atari games, the Deep Q Networks should be able to solve our environment. To tackle the computational complexity of the DQN algorithm, we propose a slight change in the architecture of the neural network.

The Neural Network Architecture consists 175 input nodes. The step function of our environment returns a 35*5 numpy array having the following information:

    - Boolean (0/1) : Specifying if the info stored in this row corresponds to a berry
    - Float : The X and Y coordinate of the berry present in the 1920*1080 pixel window visible to the agent
    - Float : Specifying the distance from the agent to the berry
    - Float : Specifying the size of the berry


<h2> Documentation </h2>

There are 3 folders. The Foraging-in-a-field environment folder is the work done during the first milestone. 

The Foraging-in-a-field-Dibyo is the future prospect of the project - extending it to DDQN/Per-DQN and curiousity search. 

The Foraging-in-a-field-Main is the work implemented. NewDQN.py is the main file which bought the results. Please tweak the values accordingly for the results. DQN is also implemented in DQNPytorch.py but the main file for the DQN implementation is NewDQN.py

get_env.py initiates or declares the gym environment.

Heuristic agent is implemented in heuristic_agent.py

Data of Berries and Patches are pre-defined under the data folder.

<h2>For the Environment - (berry_field_mat_input_env.py)</h2> 


"unordered", "ordered", "buckets" are three defferent observation types that are supported.
   
"unordered", "ordered" are a 40x5 matrix with the columns as: "iS_berry", "unitvector_x", "unitvector_y", "distance", "size_of_berry"
 
unordered observation type:
 - append information into the 40x5 matrix in as the berry are detected.

ordered observation type:
 - take the unordered observation and sort the berries in clockwise sense.

buckets observation type:
 - divides the obsrvtion space into num_buckets number of equi-angular segments.
 - output matrix of shape (num_buckets, 2) with the collumns as "average-size-of-berry", "average-distance-to-berry". 
 - each row in a matrix represnts the corresponding segment in clockwise order.
 - if there is no berry in an angular segment, the corresponding row contains all zeros
 