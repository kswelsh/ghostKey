<h1 align="center">Ghost Key</h1>
<p align="center">A Simple Linux Kernel Module Keylogger</p>

## Features
:computer: Print User Input to Dmesg <br />
:computer: Reognize When a User will Type in Their Password <br />
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
to a seprate server, rather, it prints to the same device in which the module is located on. <br />

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

