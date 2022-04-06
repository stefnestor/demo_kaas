# Enable Long Path Support on Windows

\*Source: *

## Registry Edit

````regedit
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\FileSystem]
"LongPathsEnabled"=dword:00000001
````

## PowerShell

````powershell
Set-ItemProperty 'HKLM:\SYSTEM\CurrentControlSet\Control\FileSystem' -Name 'LongPathsEnabled' -Value 1
````

---

## Appendix: Links

* *Code*
* [Development](../../../MOCs/Development.md)
* *Windows*
* [Microsoft DOS](../../../../3-Resources/Tools/Developer%20Tools/Shell/Microsoft%20DOS.md)
* *Command Line*
* [2-Areas/MOCs/PowerShell](../../../MOCs/PowerShell.md)

*Backlinks:*

````dataview
list from [[Enable Long Path Support on Windows]] AND -"Changelog"
````
