# Install Azure-CLI

\*Source: *

````powershell
$ProgressPreference = 'SilentlyContinue'; Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi
Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'
Remove-Item .\AzureCLI.msi
````

---

## Appendix: Links

* *Code*
* [2-Areas/MOCs/PowerShell](../../../MOCs/PowerShell.md)
* *Azure CLI*
* [Development](../../../MOCs/Development.md)

*Backlinks:*

````dataview
list from [[Install Azure-CLI]] AND -"Changelog"
````
