## Understanding of async in at it's foundation aand implentation in the most basic form  
Like me you probably are also used to  he most used and popular model of writing and running code, which is in the sequential manner. It is how i was thought about algorithms. The idea that the computer understood the instructions in this way and how it has to evaluate code line by line, the sequential way.Now ideally this is how the code is interpreted or insome othet cases compiled. This piece is more about how the code runs , as for other purposes you may want to run code differently. You may want your instructions to be performed in a not so sequential manner ie  requires tht one process be done before another can start. 
For this reason we could write our code  to run in a  different manner using a different model . We could implement an asynchronous solution and this will have a whole new effect on how our code runs and how task is accomplished. 
And what this means basically is instead of our code running in a way we are used to that is each process running after the other, we can have two different processes run side by side. 
Yes i know very awesome stuff. Making code run asychronously is nothing new or as complicted now . in fact you have libraries that make this possible which jsut a few lines of code. eg:  using async libries like pythons asyncio or curio or you could even use threads to achieve this. This is nothing new 

### However..
purpose of this piece is to document or should i say put my understanding of my recent learnings of asychronous code and implementation of concurrency in code without any libraries and threads.I learned about the foundation and core concepts relating to how async libraries like asyncio are archetectured to work the way they do. 
I shall break down my understanding in 2 paragraphs and perharps attach some few lines of code for support. I shall address the basic idea on how to make two process in this case functions run side by side using callbacks and genrators in python.

### doing concurency with callback function method - foundational idea and concept 
Ok, in a scenario where we have to functions that perform a series of actions and finish at point. If we want these functions to process or run concurrently we shall have set them up in a special manner to do so. We do not want one function running while one remains idle , no, in our situation we want to see both running at the same time or side by side/
So lets considder it

In the most basic level, what we need is a scheduler which shall be an object that will cordinate our fuctions execution flow.
we shall define a scheduler class in python with some properties and methods which will help cordinate our functions in a way that will reflect concurrency.

Now our scheduler class, soon to turn object shall have properties like a `ready queue`(we could use a list to make things simple), and another queue called `sleeping`.
we shall also have a few methods in this case . we could add a method called `call_now` , `call_later` and a `run` method.

Now i shall explain what these properties and functions do while at the same time explaining how this scheduler object can help run processees concurrently.


#### ready queue
The `ready` queue shall contain all processes or functions that are ready to run.

### sleeping queue
The `sleeping` queue shall contain process that are not ready to run.a delay perharps or lag.  

### call_next 
The `call_next` method shall append processes/functions into the ready queue to be run and the 

## call_later 
`call_later` shall schedule fucntions to be run when ready. Now we need this as this helps in  a situation of how  we can prevent one process from interferring with the other allowing the delay of one process not too affect the execution of the other  . 

### run
The `run` method is implemented as a while loop that checks the ready and sleeping queue in each iteration. If there is nothing in the ready queue, ie if there are no functions to run. We check the sleeping queue and pop out a process  which is likely to be ready soon. Wait for it to be ready then append it to the ready queue.  The run method on each iterarion runs a function and provided there are some in the ready queue.
Again, the  idea of having a sleeping queue which is sorted according to which function or process is done first allows the delay of certain process not to affect the others. The get run as at the time ther are ready .
`eg:` if you have two processes being coordinated by our scheduler object. Supposed one takes 1 sec to complete each step of its task and the other 5 secs . That means the first one completes in 5 seconds 5 tasks and in the same time the second one does one task . No waiting happens. This is what the concept of a sleeping queue brings. regardless without it , we can still have our functions run side by side 


