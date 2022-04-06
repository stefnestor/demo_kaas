# DISM Commands

\*Source: *

* `DISM` Scan Health:

````powershell
Dism /Online /Cleanup-Image /ScanHealth
````

* `DISM` component cleanup:

````powershell
Dism.exe /online /Cleanup-Image /StartComponentCleanup
````

* DISM online repair image

````powershell
Dism /Online /Cleanup-Image /RestoreHealth
````

* DISM online repair image with [2-Areas/MOCs/PowerShell](../../../MOCs/PowerShell.md) cmdlet:

````powershell
Repair-WindowsImage -Online -RestoreHealth
````

* DISM online repair image

````powershell
Repair-WindowsImage -Online -RestoreHealth
````

* DISM online repair image

````powershell

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
list from [[DISM Commands]] AND -"Changelog"
````
