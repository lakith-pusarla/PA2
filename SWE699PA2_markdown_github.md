# SWE 699 PA 2
## Team: Neural Nexus
##### Anish Kumar Saranga           G01376251
##### Ayaan Ehsaan Mohammad         G01355098
##### Murali Sai Lakith Pusarla     G01381718
-------------
### Steps before executing code:


- Run pip install z3-solver
- Run python se.py using command 'python se.py' or 'python3 se.py'(this will execute test1() and test2())

 ### Answers to the given questions:
1. Briefly describe what you did for part 1 and part 2.

    a. Part 1:
    
        - The algorithm accepts an encoded DNN and an 'inputs' argument which by default takes two real Z3 variables as input nodes. This can be generalized by calling the function by passing the specific number of input neurons to the 'inputs' parameter.
        - The functions 'create_random_nn()' and 'get_hidden_and_output_nodes()' help create a dnn with random weights and bias values (both within the range [-5, 5]).
        - The my_symbolic_execution function symbolically executes a Deep Neural Network (DNN) using the Z3 package in Python. It calculates the symbolic expressions representing the DNN's behavior, including ReLU activation, and records them as constraints. The function then measures the runtime of this symbolic execution and outputs the results. The function acts as a powerful tool for analyzing and verifying DNN behavior without performing actual computations.
        - The symbolic_states variable keeps track of outputs of all the neurons. Each layer is tracked using the layer_states variable and then finally returns the 'z3.And'ed version of all items of symbolic_states.
        - Once this is done, we are checking for the assertion of the created DNN and it works perfectly.
    b. Part 2:
    
        - We defined a function named my_interval_execution that serves the purpose of estimating the potential output ranges for individual nodes within a deep neural network (DNN). The process involves iterating through each layer of the DNN, considering the weights, biases, and activation functions applied to each node. 
        - Input ranges for these nodes are assumed to be stored in the pre dictionary. 
        - For each layer, the code calculates the potential output range for every node by multiplying the input ranges with their corresponding weights, summing the results, adding the node's bias, and, if the activation function is ReLU, applying the rectified linear unit activation. The code then assigns a variable name to each node based on its position within the network, such as "n01" for the first node in the second layer. 
        - The calculated node ranges are stored in the all_node_ranges dictionary, which is updated with each layer's results. Once all layers are processed, the function returns all_node_ranges, which contains the input and output range information for all nodes in the neural network. 
        - We essentially implemented a range propagation algorithm, allowing us to analyze the potential output ranges of individual nodes in a neural network, which can be valuable for understanding the network's behavior and uncertainty.
        - Once this is done, we checked for the assertion. For a DNN with a size of 4, we have verified it onpaper
        
2. Describe the plots and conclusions you have for scalability of both parts 1 and 2
   
   We have plotted the DNN size vs Execution time graph with the Execution time value in seconds.
   
    a. Part 1 (Symbolic Execution):
    
    	- Symbolic execution takes almost similar time for executing DNNs until the size of 256 and then we see a gradual increase until DNN size is 387420489.
    	- Later sizes shows little reduction and then a sharp increase.
    	- For any DNNs with larger sizes, execution only takes longer and the graph keeps increasing exponentially.
    	
    b. Part 2 (Abstract Execution):
    
    	- Abstract execution takes almost the same time for every size of DNN.
    	- For really large size of DNNs, the execution time increases but the rate of change is very low and the curve increases slowly. 
    	- There is no siginificant difference in the execution times for increasing sizes of DNNs.

![Test image](https://github.com/lakith-pusarla/PA2/blob/main/comparision_plot.png)

3. What do you think the most difficult part of this assignment?
	
    The most difficult part of this assignment was to write the code for Abstract execution. We were able to understand the concept and an example on paper, but to write the code for it was a streneous task. Building the code while keeping the flow of logic intact took a lot of time. Once this was done, rest of the taks were completed relatively fast.
    
4. What advice do you give other students (e.g., students in this class next year) about this PA?

	Our advice would be to be clear with the problem on paper. It is not advisable to copy code from internet and tweak it until you get the output. Try not to start with the generalized code, instead write a code that satisfies the initial example, and then build upon it for a generalized solution.


