### How does the DevBoard handle received serial messages? How does this differ from the naïve approach?
The devboard recieves signals through a triggered events, which flags whenever a signal is recieved, known as the interpretter. The naive one differs by continously checking for an incoming signal instead of checking for a flag.

### What does `detached_callback` do? What would happen if it wasn't used?
The detached callback function allows all registered callbacks to spawn detached threads by marking their spawns with a decorator. This is to avoid one thread freezing up and stalling the entire program. If it wouldnt used, it would be a regular occurance for the serial code to get stuck and stop the functionality of our program for that time.

### What does `LockedSerial` do? Why is it _necessary_?
Since we are multithreading, there is a chance that more than one thread may try to use the serial port at the same time, which would cause issues such as race conditions, which is where the behavior is determined by uncontrollable timing events. To avoid this, we use the locked serial function, which prevents entry into the serial port while it is in use.