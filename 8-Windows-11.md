## Chapter 8) Windows 11 Installation & Upgrades

### Installing Windows 11 is not natively supported on Surface computers with 7th gen or lower processors. 
### The instructions below will walk you through how to "Clean" install Windows 11 as well as how to "Upgrade" from Windows 10 to 11 and between builds once Windows 11 is installed.
### The instructions below will also allow changing to an "Windows Insider" release withought needing to sign up for it and with better options for switching between them or back to general release.
Some of the work and links provided below are work provided by: [Credit: abbodi1406](https://github.com/abbodi1406), [Credit: AveYo](https://github.com/AveYo). Where reasonable, I have provided links to their work to ensure everything remains current.




### Clean Install of Windows 11:
1. Download the latest version of "Rufus" from https://rufus.ie/
2. If you already have a Windows 11 iso file skip to step 5 otherwise start Rufus select the dropdown to the right of the ```"SELECT"``` button and then click ```"Download"```.
3. Press the ```"Download"``` button.
4. It may take a second the first time but once the ```"Download ISO Image"``` pop up launches select the following options clicking ```"Continue"``` after each selection: ```"Windows 11" --> "Release" (Choose the most recent) --> "Edition" (Leave default) --> "Language" (Your preferred language) --> "Architecture" (your preferred architecture) --> Click "Download"```
5. If you already had an ISO image downloaded, click ```"Select"``` and choose your file. At this point regardless of downloading or selecting and ISO you already had, most options will now be pre-selected though we need to change a couple.
6. Choose your device you would like to write the Windows 11 image to from the drop down. 
7. Click the drop down under ```"Image Option"``` and select ```"Extended Windows 11 Installation (no TPM / no Secure Boot)"```
8. Adjust other settings if needed and then click ```"Start"```
9. This will take a few minutes depending on the speed of the drive. Once completed you can restart from the USB/SD card and perform a clean install. 
10. Once the install of Windows 11 has completed you will need to install the One Mix 4 drivers for the Rotation sensor in order for the rotation sensor and keyboard shut off to work properly as the default Windows drivers will not work properly.


### Upgrade from Windows 10 to Windows 11:
1. Create a new text file named: 
   ```
   Skip_TPM_Check_on_Dynamic_Update.cmd
   ```
2. Open the text file you just created and copy text from [Here](https://github.com/AveYo/MediaCreationTool.bat/blob/main/bypass11/Skip_TPM_Check_on_Dynamic_Update.cmd). Code provided below for convenience. Save the file.
   ```
   @(set "0=%~f0"^)#) & powershell -nop -c iex([io.file]::ReadAllText($env:0)) & exit/b
    #:: double-click to run or just copy-paste into powershell - it's a standalone hybrid script

    #:: v7 dynamically skips the anti-consumer windows 11 setup checks via /Product Server trick  
    #:: it is most reliable, and only has a 'Windows Server' label cosmetic-ish difference
    #:: works with:
    #:: 11 setup via Windows Update (after using OfflineInsiderEnroll by whatever127 and abbodi1406)
    #:: 11 setup via mounted iso / usb (use the Quick.. script for skipping 11 setup checks at boot)

    $_Paste_in_Powershell = { $Code = @'
    $Nfo = 'Skip TPM Check on Dynamic Update v7, AveYo 2021'
    $Arg = (([environment]::get_CommandLine()-split'-[-]% ')[1]-split'.exe[\p{P}]? ')[1]
    foreach ($x in 'Product','DynamicUpdate','Telemetry') {$Arg = $Arg -replace $('\p{P}?/'+ $x +'\p{P}? \p{P}?[A-Z]+\p{P}? '),' '}
    $Cli = ' /DynamicUpdate Disable /Telemetry Disable ' + $Arg; $Srv = ' /Product Server' + $Cli
    $Dir = join-path $([Environment]::SystemDirectory[0..2]-join'') '$WINDOWS.~BT\Sources\'
    $Cfg = join-path $Dir 'EI.cfg'; $EI = '[Channel]' +[char]13+[char]10+ '_Default' +[char]13+[char]10
    $Exe = join-path $Dir 'SetupHost.exe'; $Inf = get-item -force -lit $Exe; [int]$Ver = $Inf.VersionInfo.FileBuildPart
    if ($Ver -ge 22000) {$Run = $Exe + $Srv} else {$Run = $Exe + $Cli}
    if ($Ver -ge 22000 -and !(test-path $Cfg)) {[io.file]::WriteAllText($Cfg, $EI)}

    $D=@(); $T=@(); $A=@(); $M=[AppDomain]::CurrentDomain.DefineDynamicAssembly(1,1).DefineDynamicModule(1) 
    foreach ($x in 0..2) {$D+=$M.DefineType('AveYo_'+$x,1179913,[ValueType])}; foreach ($x in 1..2) {$D+=$D[$x].MakeByRefType()}
    $S=[string]; $I=[int32]; $U=[uintptr]; $y=0; $z=0;  foreach ($x in $U,$U,$I,$I) {$9=$D[2].DefineField('f'+$y++,$x,6)}
    foreach ($x in $I,$S,$S,$S,$I,$I,$I,$I,$I,$I,$I,$I,[int16],[int16],$U,$U,$U,$U) {$9=$D[1].DefineField('f'+$z++,$x,6)}
    $9=$D[0].DefinePInvokeMethod('CreateProcess','kernel32',8214,1,[void],($S,$S,$I,$I,[bool],$I,$I,$S,$D[3],$D[4]),1,4)
    $9=$D[0].DefinePInvokeMethod('DebugActiveProcessStop','kernel32',8214,1,[void],($I),1,4)
    foreach ($x in 0..2) {$T+=$D[$x].CreateType()}; foreach ($x in 1..2) {$A+=[Activator]::CreateInstance($T[$x])}
    $R=$null, $Run, $null, $null, $false, 0x02000011, $null, $null, $A[0], $A[1] 
    $T[0].GetMethod('CreateProcess').invoke(0, $R); $T[0].GetMethod('DebugActiveProcessStop').invoke(0, $R[9].f2)
    $W=get-process -pid $R[9].f2 -ea 0; for (;;) {sleep 1; if (0-eq $R[9].f2 -or $null-eq $W -or $W.HasExited) {return} }
    '@ -replace '\r?\n|\r', '; ' <# lines 20-29 are needed for escaping ifeo, remain calm ;) #>  

    $IFEO = 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\SetupHost.exe'
    $Prog = join-path $([Environment]::SystemDirectory[0..2] -join '') '$WINDOWS.~BT\Sources\SetupHost.exe'
    $Skip = "powershell -win 1 -nop -c iex (get-itemproperty '$IFEO\0' 'Code' -ea 0).Code; write-host --%"
    if (test-path "$IFEO\0") {
      remove-item $IFEO -rec -force -ea 0 >''
      write-host -fore 0xf -back 0xd "`n Skip TPM Check on Dynamic Update v7 [REMOVED] run again to install " 
     } else {                              
       new-item "$IFEO\0" -force -ea 0 >'' 
       set-itemproperty "$IFEO\0" 'Debugger' $Skip -force -ea 0; set-itemproperty "$IFEO\0" 'Code' $Code -force -ea 0
       set-itemproperty "$IFEO\0" 'FilterFullPath' $Prog -force -ea 0; set-itemproperty $IFEO 'UseFilter' 1 -type dword -force -ea 0
       write-host -fore 0xf -back 0x2 "`n Skip TPM Check on Dynamic Update v7 [INSTALLED] run again to remove "
     } 
     remove-item $($IFEO -replace 'SetupHost', 'vdsldr') -rec -force -ea 0 >''; rmdir (split-path $Prog) -rec -force -ea 0 >''
     $N = 'Skip TPM Check on Dynamic Update' <# also remove wmi-based v1 if somehow still installed, not just vdsldr-based v2 - v5 #>
     $U = 'root\subscription'; $C = gwmi -Class CommandLineEventConsumer -Namespace $U -Filter "Name='$N'" -ea 0 
     $B = gwmi -Class __FilterToConsumerBinding -Namespace $U -Filter "Filter = ""__eventfilter.name='$N'""" -ea 0
     $F = gwmi -Class __EventFilter -NameSpace $U -Filter "Name='$N'" -ea 0; $B,$C,$F |% {$_|rwmi -ea 0}; timeout /t 5
    } ; start -verb runas powershell -args "-nop -c & {`n`n$($_Paste_in_Powershell-replace'"','\"')}"
    $_Press_Enter
    #::
    ```

3. Run the file you just created with Administrative permissions. If it does not run or you don't have the option, confirm the file doesn't have the ```".txt"``` extention after ```".cmd"```. 
4. If you want to reverse the changes made in this file, simply re-run the script with administrative permisions and your computer will be returned to normal.
5. In some cases Windows 11 may not show up right away or may still appear to be unavailable. In order to initiate an update right away continue with step 6. If the Windows 11 update appears and permits updating right away you can stop here.
6. If Windows 11 is still not available for upgrading go [Here](https://github.com/abbodi1406/offlineinsiderenroll/releases) and download the latest release of ```"OfflineInsiderEnroll"```.
7. Run ```"OfflineInsiderEnroll.cmd"``` with administrative rights
8. If you want to simply update to Windows 11 select ```"Enroll in Beta Channel"```. It is possible that this option may change in the future. You may also choose to enroll into the Dev channel though you should expect some issues with those releases.
9. Restart the computer as required by the script
10. Run Windows Update and Windows 11 should now download.
11. Once Windows has upgraded to Windows 11 you should repeat steps ```7 through 9``` but this time select ```"Stop Receiving Insider Preview Builds"```.
12. Restart the computer as required by the script.
13. Congratulations, you now should be on the regular release of Windows 11 and will continue to receive updates as normal. If you experience issues updating repeat step 2 or confirm the script hasn't been updated by going to the host link also provided in Step 2.


### Changing from Regular Windows Releases to "Release Preview", "Beta Channel", or "Dev Channel". 
If on Windows 10:
Repeat steps: ``` 6 through 10 ``` selecting the channel you want in step 8.

If on Windows 11 or upgrading from Windows 10 to 11 and wanting to stay on a "Beta" or "Dev" channel:
If you have not already run the ```"Skip_TPM_Check_on_Dynamic_Update.cmd"``` script, complete steps ```1 through 10```, selecting either the "Beta" or "Dev" channel builds in step 8. (Release Preview cannot be selected until you have moved to Windows 11); otherwise, only complete steps ```6 through 10```, selecting the channel you want in step 8.




