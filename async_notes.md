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

our


