## JavaScript Code Execution

When you run JavaScript code, a Global Execution Context is created
Link:-  [[1- How JavaScript Works]]  
The Execution Context phase is created in two phases. 
1. First, Memory phase is created
	In memory creation phase, we are allocating memory to all the variables and 
	`undefined` is assigned to all the `variabes` of code.
	and if there is some function, all of its body is assigned to the name of function.
2. In second phase, JavaScript program will start assigning actual values to the variables and do the calculations.  Whenever a function is invoked, execution context is created inside the Global Code block which have memory and code. When function is returned, the function code context is deleted.


#### Call Stack
Call Stack is used for managing the Execution Contexts. 
It has Global Execution Context at the bottom. When a function from Global Execution Context is invoked, another Execution Context created for that specific Function is pushed to Call Stack and once that code inside functions execution context is finished, it is deleted. and returned back to the line from where function was invoked. 