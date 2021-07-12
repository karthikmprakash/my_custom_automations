# Windows Automation and Useful Scripts


## Custom `touch` command for Windows 
All linux programmers love `touch` command, its the fastest way to create multiple files at once. Here's a way to replicate the touch command on Windows using Batch Scripts.
Its quick and easy to setup.

create a new text file, paste the below script and save it as `touch.bat `

```batch 
@ECHO OFF

SET PARAMS=

:_PARAMS_LOOP

REM There is a trailing space in the next line; it is there for formatting.
SET PARAMS=%PARAMS%%1 
ECHO.> %1
SHIFT

IF NOT "%1"=="" GOTO _PARAMS_LOOP
```

now to use or access the bat scripts from anywhere on the system its necessary we [add the path](https://java.com/en/download/help/path.html) to the file in the system variables.
