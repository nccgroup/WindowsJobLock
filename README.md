Windows Process Lockdown Using Job Objects
======================

A collection of tools to enumerate and analyse Windows DACLs

Released as open source by NCC Group Plc - http://www.nccgroup.com/

Developed by Ollie Whitehouse, ollie dot whitehouse at nccgroup dot com

https://github.com/nccgroup/WindowsDACLEnumProject

Released under AGPL see LICENSE for more information

Overview of Windows Jobs Objects
-------------
Read - http://msdn.microsoft.com/en-us/library/windows/desktop/ms684161(v=vs.85).aspx<br>
Chrome's use - http://src.chromium.org/viewvc/chrome/trunk/src/sandbox/win/src/job.cc

What it can do
-------------
```
[*] A Microsoft Windows Process Lockdown Tool using Job Objects - https://github.com/nccgroup/WindowsJobLock
[*] NCC Group Plc - http://www.nccgroup.com/
[*] -h for help
    i.e. Win.JobLock.exe [-h]

 [.General Settings / Options.]
    -g          - Get process list
    -P <name>   - Process name to apply the job to
    -p <PID>    - PID to apply the job to
    -n <name>   - What the job will be called (optional)
 [.Process Limits.]
    -l <number> - Limit the number of process to this many
 [.Memory.]
    -m <bytes>  - Limit the total memory in bytes for the entire job
    -M <bytes>  - Limit the total memory in bytes for each process in the job
 [.Process Control.]
    -k          - Kill all process when the job handle dies
    -B          - Allow child process to be created with CREATE_BREAKAWAY_FROM_JOB (weak security)
    -b          - Allow child process which aren't part of the job (weak security)
 [.UI Security Controls.]
    -d          - Prevent processes within the job from switching or creating desktops
    -D          - Prevent processes within the job from calling the change display setting function
    -x          - Prevent processes within job from calling the exit Windows function
    -a          - Prevent processes within job from accessing global atoms
    -u          - Prevent processes within job from user user handles
    -c          - Prevent processes within job from reading the clipboard
    -s          - Prevent processes within job from changing system parameters
    -C          - Prevent processes within job from writing the clipboard
```

Example
-------------
This example will stop you from being able to paste into Notepad or it from spawning other processes :)
```
C:\>Win.JobLock.exe -P notepad.exe -c -l 1
[*] A Microsoft Windows Process Lockdown Tool using Job Objects - https://github.com/nccgroup/WindowsJobLock
[*] NCC Group Plc - http://www.nccgroup.com/
[*] -h for help
[*] Opened process notepad.exe
[i] Process Limit                 - True  - 1
[i] Job Memory Limit              - False - 0
[i] Process Memory Limit          - False - 0
[i] Kill Process on Job Close     - False
[i] Break Away from Job OK        - False
[i] Silent Break Away from Job OK - False
[i] Limit Desktop Operations      - False
[i] Limit Display Changes         - False
[i] Limit Exit Windows            - False
[i] Limit Global Atoms            - False
[i] Limit User Handles            - False
[i] Limit Reading of Clipboard    - True
[i] Limit System Parameter Change - False
[i] Limit Writing to Clipboard    - False
[i] Final job name                - NONAME
[*] Applied job exended limits to job object
[*] Applied UI limits to job object
[*] Applied UI limits to job object
[*] Applied job object to process!
[*] Successfully built and deployed job object to notepad.exe!
```

