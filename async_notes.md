## Understanding of async in at it's  foundation aand implentation  in the most basic form  
Like me you probably are also used to the perharps the most used and famous model of wrting and running code , which is in the sequential manner. it is how i was thought about algorithms . the idea that the computer understood the instructions in this way and how it has to evaluate code line bt line, The sequential way. But for other purposes that you may want to run code differently. you may want your instructions to be performed in a different manner and not the regular sequential way which requires tht one process be done before another can start. 
for this reason we could write our code in a different manner using a different model \. we could implement an asynchronous solution and this will have a whole new effect on how our code runs and how task is accomplished. 
And what this means basically is instead of our code running in a way we are used to that is each process running after the other to an eextent , making the process asychronous will have our process happen side by side so as to say.
definitely sounds awesome.
Essentially there are ways you could make code asnchronous using async libries like pythons asyncio or curio or you could even use threads to achieve this. this is nothing new 

### However..

purpose of this piece is to document or should i say put my unnderstanding  of my recent learnings of asychronous code and implementation of concurrency in code without any libraries and threads.I learned about the foundation and core concepts relating to how async libraries like asyncio are archetectured to work the way they do 

i shall break down my understanding in 2 paragraphs and perharps attach some few lines of code for support. i shall address the basic idea on how to make two process in this case functions run side by side using callbacks and genrators in python.

### doing concurency with callback function method - foundational idea and concept 
i  a scnenario where we have to functions that perform a series of actions and finish at point . if we want these functions to process or run concurrently we shall have set them up in a special manner to do so. we do not want one function running while one remains idle , no .
so lets considder it

in the most basoc level , what we need is acheduler , which shall be an object.
we shall define a scheduler class in python with some properties and methods which will help cordinate our functions or actions in a way that will reflect concurrency ,

Now our scheduler class , soon to turn object shall have properties like a `ready queue`(we couldd use a list to make things simple), and another queue called `sleeping`.
we shall also have a few methods in this case . we could add a method called `call_net` and `call_later` and a `run` method.

Now i shall explain what these properties and functions do while at the same time explaining how this scheduler object can help run processees concurrently.

the `ready` queue shall contain all processes or functions that are ready to run, the `sleeping` queue shall contain process that are not ready to run.a delay perharps or lag.  the `call_next` method shall append processes/functions into the ready queue to be run and the `call_later` shall schedule fucntions to be run when ready . Now the driving force of this concept and how we can prevent one process from interferring with the othet allowing these processes to run side by side is the `run` method in the scheduler object . 

the `run` method is implemented as a while loop that checks the ready and sleeping queue in each iteration . if there is nothing in the ready queue , that is if there are no functions to run. we check the sleeping queue and pop out a process  which is likely to be ready soon . wait for it to be ready then append it to the ready queue.  the run method on each iterarion runs and process provided there are some in the ready queue.
the idea of having a sleeping queue which is sorted according to which function or process is done first allows the delay of certain process not to affect the others . they get run as at the time ther are ready .

ecample , if you have two processes being cordinatted our scheduler object . supposed one takes 1 second to complete each step of its task and the other 5secs . that means te first one completes in 5 seconds  5 tasks and i the same time the second one does one task . no waiting happens . the happen withing the same 5 seconds side by side .


