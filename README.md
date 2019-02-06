## About
This batch file has been created to address Windows 10 issues with Chrome and other apps being slowed down by Windows, as discussed in this thread: 
https://productforums.google.com/forum/?utm_medium=email&utm_source=footer#!msg/chrome/3OJC764nVQs/Ce6xsBlBAgAJ

## Instructions
1. Download this .bat file and store it somewhere on your computer.  
2. Run the batch file as administrator  
  a. **Single use**: Whenever you want to stop the service, execute the batch file as administrator.  
  b. **Automatic recurring use**:  
    - i. From the start menu, type "Task Scheduler" and open it as administrator. If you cannot open it due to an error message, try the steps outlind in "Failed to open Task Scheduler" in the "Troubleshooting" section.
    - ii. Open the "Action" menu and select "Create Task".  
    - iii. In the 'General" tab, set "name" to whatever you like, for example: "cryptographic_services_stopper"
    - iv. Optional: Check the option "run whether user is logged on or not"
    - v. Optional: Check the option "run with highest privileges"
    - vi. Click the "configure for" menu and select  "Windows 10"
    - vii. Optional: Open the "Conditions" tab, and uncheck the option "start the task only if the computr is on AC power"
    - ix. Open the "Actions" tab, and click "New".
    - x. In the new actions dialogue box, set "Action" to "Start a program".
    - xi. Under "Settings", set the value of "program/script" to `PATH/TO/cryptographic_services_stopper.bat`, where "PATH/TO" is the path on your system where you have stored the batch file. Click OK.
    - xii. Open the "Triggers" tab, and click "new".
    - xiii. Set the option "Begin the task" to "at log on".
    - xiv. Optional: Set the "Settings" to "any user".
    - xv. Under advanced settings, set "repeat task every" to whatever you like, for example: "15 minutes".
    - xvi. Set "for the duration of" to "indefinitely".
    - xvii. Optional: Set "Stop task if it rungs longer than" to "30 minutes"
    - xviii. Set to be "enabled".
    - xix. Optional: Set "Activate" to the current date and time.
    - xx. Click "OK". If it asks you for a password, enter your administrator password. If you have not set a password yet, you can set one by opening the Start menu and typing "Sign-in options", opening that, and clicking "Add" under the password section. Make sure to keep record of this password somewhere safe.

## Possible side effects
### Permanent 'UAC Errors'
It is possible that, when stopping Cryptographic Services, you will occasionally receive recurring issue where when you try to open a certain system program or access certain system settings, you will see the following error appear:

![uac_error.png](docs/static/uac_error.png)

> **This app has been blocked for your production**
> An administrator has blocked you from running this app. For more information, contact the administrator.
> `mmc.exe`
_...and so on_

At the moment, I am not sure how to resolve this issue for good while the Cryptographic Services service is stopped.

## Troubleshooting
### Failed to open Task Scheduler
When trying to open the task scheduler to run this batch script on a regular basis, you may receive the error "UAC Error" as described in the "Possible side effects sections"

Take the following steps to attempt to solve this issue:
1. Try activating administrator and opening again on your regular Windows account
To resolve this issue, open cmd or powershell as administrator, and execute the following line:

`net user administrator /active:yes`

2. Try deactivating administrator and opening again on your regular Windows account
Open cmd or powershell as administrator, and execute the following line:

`net user administrator /active:no`

3. Create the task after logging in as the "Administrator" user
_These steps have been sourced from this video: https://www.youtube.com/watch?v=VDA1URdYRME _

- Follow step (1) again, activating the user administrator.
- Sign out from Windows
- From the Windows log-in screen, sign in as "Administrator"
- Open Task Scheduler (e.g. by opening the start menu, typing "Task Scheduler", and clicking to open).
- Continue the steps discussed in the "Instructions"
