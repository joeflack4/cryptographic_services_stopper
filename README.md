## About this file
It addresses issues with Chrome and other apps being slowed down by Windows, as discussed in this thread: 
https://productforums.google.com/forum/?utm_medium=email&utm_source=footer#!msg/chrome/3OJC764nVQs/Ce6xsBlBAgAJ

## Instructions
1. Download this .bat file and store it somewhere on your computer.
2. Set up a cronjob to regularly execute it, making sure it runs as administrator.
  2a. From the start menu, type "Task Scheduler" and open it as administrator.

## Possible side effects


## Troubleshooting
### Failed to open Task Scheduler
You may see a notice appear that says "This app has been blocked for your production", "An administrator has 
blocked you from running this app. For more informatoin, contact the administrator." "mmc.exe", and so on.

To resolve this issue, open cmd or powershell as administrator, and execute the following line:

`net user administrator /active:yes`

If you still cannot load Task Scheduler, restart your computer. If it still doesn't work, open cmd or powershell 
as administrator, and execute the following line:

`net user administrator /active:no`

If that still doesn't work...

![uac_error.png](docs/static/uac_error.png)
