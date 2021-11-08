<h1 align="center">Ghost Key</h1>
<p align="center">A Simple Linux Kernel Module Keylogger</p>

## Features
:computer: Print User Input to Dmesg <br />
:computer: Recognize When a User will Type in Their Password <br />
:computer: Simple Code for a Kernel Space Interrupt Handler <br />

## Purpose
The purpose of this project is to simply better understand Linux Modules, as well as Linux module code. Through
this project, which was our term long project in Operating Systems at NCC college, one can gain a better understanding
of Linux Kernel Modules and interrupt handlers in Kernel Space.

## Important Information
It is important to note that normally in an interrupt handler pr_info() should not be used. This causes minor issues
in our key logger, however, these issues are not large enough to enable us to create a solution. This project
could be imporved upon by threading our kernel module, as well as printing output to a seperate server. If one would
actually want to get a users passcode, they must add functionality to this module, as it does not yet print output
to a seperate server, rather, it prints to the same device in which the module is located on. <br />

## Understanding the Code
  - 28/29: Needed for module and kernel functionality.<br />
  - 31: Needed for an interupt handler.<br />
  - 32: Needed for the INB() function call.<br />
  - 36: The interrupt line needed to access the built keyboard on a machine.<br />
  - 39: The data register which keyboard pressed are stored.<br />
  - 43/45: Numbers to use in terinary operations to achieve just the exact bit needed for operations.<br />
  - Declarations: All declartions explaned in source code.<br />
  - 74: Irqreturn_t is the return value of the interrupt handlers, used to obtain key values.<br />
  - 81-189:
    - The functionality of the interrupt handler is as follows: On key press, the function will test to see if the key pressed
      is part of the word "sudo" if so, it will go through a series of checks to see if "sudo" was typed. After this, if 'enter'
      is pressed, it will begin recording key presses, as that is where the password is located. Once 'enter' is pressed a second
      time, it will stop recording and print out the password to dmesg.<br />
  - 195-402:
    - The functionality of this section is mainly declartions of all the keys. This code is executed during the initilization
      of the Linux Module. Initilization of the corresponding arrays is done this way for redability. Finally, on line 401, our
      interrupt handler is set up. The passed in variables are explained throughout the code on 395-400.<br />
  - 406-412:
    - This function is called upon exiting to free all of which is used.<br />
  - 415/418:
    - Called upon entering and exiting the Linux Module.<br />
  - 421-425: Required module information.<br />

## Using the Module
  Step 1: Clone the repo from GitHub.<br />
  Step 2: CD to the destination at which the cloned files are located.<br />
  Step 3: If you do not have the 'ghostKey.ko' file, run the 'make' command.<br />
  Step 4: Type in 'sudo insmod ghostKey.ko'<br />
  Step 5: Upon 'sudo <command> <enter>' recording will start.<br />
  Step 6: The next text typed in will be considered a password and will be stored after an 'enter' press.<br />
  Step 7: Type in 'sudo rmmod ghostKey.ko'<br />
  Step 8: To view the information 'sudo dmesg'<br />
  
## Important Note
Occasionally the printed out password will involve a certain key multiplied by a certain amount. An example of this
is the key 'a' being outputted two too many times. This seems to be an issue with pr_info() inside of a handler, as it
is somehow getting interuppted and constantly repeating the print (This is not yet confirmed, as it could also 
be an issue related to bounce on the keyboard). However, this does not stop the possibility of obtaining a users passcode.
Through extensive testing, this issue will occur in minimal amounts, depending on what is happening on your machine.
Also, this issue can be easily solved by looking at what time certain keys are pressed, as repeats are normally at inhumane speeds.
An assumption is also made that a user will type in their password correctly more times than incorrectly. To sucessfully obtain
a users password the module must be left on a machine for a significant amount of time, then data should be compared of every password input.<br />
  
## Future Updates
Since this project was done as a project for a undergraduate college-level course, we were limtied on time. However, there are more features we would
like to add over time.
  - Functionality to send the password to a server.
  - A seperate program to read through all of the data and generate a guess on what the password is.
  - Ways to hide the Linux Module on the system.
  - Ways of socially engineering the module onto someones system.
  - Threading the Linux Kernel Module
  
  
  

