# Adding a server
```powershell
set-DnsClientServerAddress -InterfaceIndex 2 -ServerAddresses ("Your.DC.IP.Address")
set-DnsClientServerAddress -InterfaceAlias Ethernet -AddressFamily IPv4 |Select-Object ServerAddresses 

$computers = Read-Host "Enter Computer Name> " 
Add-Computer -ComputerName $computers -Domain "ad.yourdomain.com" -Restart
```
This is to install a server into the ad domain
# Adding a Recycle bin to your DOMAIN
```powershell
$domain= read-host "Provide the domain name"
$DCserver = read-host "Provide DC server name"
Enable-ADOptionalFeature -Identity 'Recycle Bin Feature' -Scope ForestOrConfigurationSet -Target $domain -Server $DCserver -Confirm:$false
```
# Get details of every single computer in domain
```powershell
get-adcomputer -properties* -filter * | export-csv "provide path"
```
# Details of every single user
```powershell
get-aduser -properties* -filter * | export-csv "provide path"
```
# grab all Operating systems in the domain
```powershell
Get-ADComputer -Filter "name -like '*'" -Properties operatingSystem | group -Property operatingSystem | Select Name,Count
```
# Making Bulk AD groups
```powershell
$csv = Import-csv -Path "C:\Users\test\Desktop\groups.csv"
$name=$item.GroupName
Foreach ($item in $csv)
{
    try
{ 
    New-ADGroup -Name $item.GroupName -GroupCategory $item.GroupCategory -groupScope $item.groupScope -Path $item.OU
    Write-Host -ForeGroundColor Green "Group $($item.GroupName) created!"
}
catch
{
Write-Host "Group already exists $name"
}
}
```
simply make a list of groups like

Accounts

IT

Departments


# Fix Time on Domain Controller
```powershell
net stop w32time
w32tm /unregister
rem Disable Hyper-V Time Sync
reg add HKLM\SYSTEM\CurrentControlSet\Services\W32Time\TimeProviders\VMICTimeProvider /v Enabled /t reg_dword /d 0 
w32tm /register
net start w32time
tzutil /s "E. Australia Standard Time"
w32tm /config /syncfromflags:domhier /update
w32tm /resync 
net stop w32time
net start w32time
```
I made this because my dc kept going out of sync