# CS698R-Project-Foraging-in-a-Field-3

There are 3 folders. The Foraging-in-a-field environment folder is the work done during the first milestone. 

The Foraging-in-a-field-Dibyo is the future prospect of the project - extending it to DDQN/Per-DQN and curiousity search. 

The Foraging-in-a-field-Main is the work implemented. NewDQN.py is the main file which bought the results. Please tweak the values accordingly for the results. DQN is also implemented in DQNPytorch.py but the main file for the DQN implementation is NewDQN.py

get_env.py initiates or declares the gym environment.

Heuristic agent is implemented in heuristic_agent.py

<h2>For the Environment - (berry_field_mat_input_env.py)</h2> 


*"unordered", "ordered", "buckets" are three defferent observation types that are supported.
   
*"unordered", "ordered" are a 40x5 matrix with the columns as: "iS_berry", "unitvector_x", "unitvector_y", "distance", "size_of_berry"
 
*unordered observation type:
 - append information into the 40x5 matrix in as the berry are detected.

*ordered observation type:
 - take the unordered observation and sort the berries in clockwise sense.

*buckets observation type:
 - divides the obsrvtion space into num_buckets number of equi-angular segments.
 - output matrix of shape (num_buckets, 2) with the collumns as "average-size-of-berry", "average-distance-to-berry". 
 - each row in a matrix represnts the corresponding segment in clockwise order.
 - if there is no berry in an angular segment, the corresponding row contains all zeros
 