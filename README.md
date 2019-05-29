# touch.cmd
Windows does not natively include a touch command.  You can use any of the available public versions or you can use your own version. Save this code as touch.cmd and place it somewhere in your path

```batchfile
@echo off
    setlocal enableextensions disabledelayedexpansion
    (for %%a in (%*) do if exist "%%~a" (
        pushd "%%~dpa" && ( copy /b "%%~nxa"+,, & popd )
    ) else (
        type nul > "%%~fa"
    )) >nul 2>&1
```

It will iterate over it argument list, and for each element if it exists, update the file timestamp, else, create it.

Reference: https://stackoverflow.com/questions/30011267/windows-equivalent-of-touch-i-e-the-node-js-way-to-create-an-index-html/30019017#30019017
