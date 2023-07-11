PLEASE NOTE: All credit goes to Ben N for this solution (link: https://superuser.com/questions/1168551/turn-on-off-bluetooth-radio-adapter-from-cmd-powershell-in-windows-10/1293303#1293303)
I only uploaded it to GitHub to store it with other scripts I use day to day.

# bluetoothToggle
A script to turn ON/OFF bluetooth in WinRT env.



```
$action = New-ScheduledTaskAction -Execute 'cmd.exe' -Argument '/C C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe  C:\Users\%USERNAME%\Scripts\bluetoothToggle.ps1 -BluetoothStatus Off'
Register-ScheduledTask -Action $action -RunLevel Highest -TaskPath "MyTasks" -TaskName "toggleBluetooth OFF" -Description "Starts powershell script to disable bluetooth in WinRT"

$action = New-ScheduledTaskAction -Execute 'cmd.exe' -Argument '/C C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe  C:\Users\%USERNAME%\Scripts\bluetoothToggle.ps1 -BluetoothStatus On'
Register-ScheduledTask -Action $action -RunLevel Highest -TaskPath "MyTasks" -TaskName "toggleBluetooth ON" -Description "Starts powershell script to enable bluetooth in WinRT"
```
Remeber to set triggers. I didnt opt to add trigger to this script as New-ScheduledTaskAction does not support the triggers i use (on lock/unlock) for that you need:
https://stackoverflow.com/questions/53704188/syntax-for-execute-on-workstation-unlock
