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
- 0-21: **GENERAL**<br />
  - 8-13: Needed imports.<br />
  - 16-18: Hidden data function imports (User Created File).<br />
  - 21: Defining the client.<br />
- 26-47: **FUNCTION GETWEATHER()**<br />
  - 28-30: Get a response from the API.<br />
  - 33: Load response into dictionary.<br />
  - 36-39: Set values using the dictionary.<br />
  - 42-44: Formatting output string.<br />
  - 47: Returning output string.<br />
- 52-79: **FUNCTION MAIN()**<br />
  - 54-56: Print once bot is loaded and ready.<br />
  - 59-61: Print return of getWeather() to output in discord when '$weather' is typed.<br />
  - 64-70: Have bot join channel user is in and play rain sounds when '$rain' is typed.<br />
  - 73-76: Have bot leave channel user is in when '$stop' is typed.<br />
  - 79: Run bot using unique bot token.<br />
- 82: Run main.<br />

## Example 'secrets.py' Code

> def getToken(): <br />
>   TOKEN = "{botToken}" <br />
>   return TOKEN <br />
>
> def getAPIKey():<br />
>    KEY = "{apiKey}"<br />
>    return KEY<br />
>
> def getLocation():<br />
>    LOCATION = "{locationNum}"<br />
>    return LOCATION<br />

## Questions?
If you have any questions feel free to contact me and ask, I am always willing to answer questions and help you out!
