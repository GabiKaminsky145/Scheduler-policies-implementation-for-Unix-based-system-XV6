# Scheduler-policies-implementation-for-Unix-based-system-XV6
 
Implementation of CFS Linux scheduler and Priority scheduler on XV6 while keep the Round-Robin naive scheduler as an option to the user.

Most of the changes can be viewed  on proc.c file. To change policies it's required to call to policy system call with 0,1 or 2.

Priority scheduler is using accumulator that is updated when a process is finished is quantum time. Each process has its own priority based on the user decision when created. New processes or awakened ones are getting the minimum accumulator value from all the processes.
This scheduler enables the system to give more time quantum to high priority processes and additionally balanced the time quantum between processes.

The CFS-based scheduler is an advanced scheduler that balanced the time quantum with better efficiency. CFS scheduler is calculating the waiting time, running time, and sleep time of the process and with these details calculating ratio that indicates where the process standing in the queue line. The scheduler is selecting a process with a minimum ratio. To calculate the running time of a process we also used the clock timer of the XV6.
