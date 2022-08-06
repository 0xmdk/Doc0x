---
title: Powershell sample
---

### Create shared inbox in hybrid env with powershell from powerautomate

```powershell
Invoke-Command  -ComputerName  "your-DC-here"  -ScriptBlock {stop-Service  -Name  ADSync}

Import-Module  MSOnline

Import-Module  ActiveDirectory

$admin  =  "globaladmin-here"

$password  =  ConvertTo-SecureString  "admpws-here"  -AsPlainText  -Force

$psCred  =  New-Object  System.Management.Automation.PSCredential  -ArgumentList ($admin,  $password)

Connect-ExchangeOnline  -Credential  $psCred

Connect-MSolService  -Credential  $psCred

$PATH  =  "C:\\Users\\$user\\Desktop\\PowerAutomate\\Mailbox"

$NURF  =  Get-ChildItem  -Path  $PATH

Foreach ($nurcsv  in  $NURF){

 $NUser  =  Import-Csv  $PATH\$nurcsv

 Foreach ($u in $NUser){

 $FirstName = $u.First

 $DispName = $u.DisplayName

 $LastName = $u.Last

 $Alias = $u.Alias

 $ADLocation = $u.ADLocation

 $MboxMembers = $u.Mboxmember,$u.Addmbxmember1,$u.Addmbxmember2,$u.Addmbxmember3

 $emailaddr  =  "$Alias@creativegroupinc.com"

 $emailaddr2  =  "$Alias@creativegroupinc2.mail.onmicrosoft.com"

 $smtprox  =  "SMTP:$emailaddr2"

 if ($adlocation  -eq  "Client Mailboxes - West"){

 $addn  =  "OU=SFO Service Accounts,OU=SFO,DC=creativegroupinc,DC=com"

 }elseif ($ADLocation  -eq  "Client Mailboxes - Central"){

 $addn  =  "OU=Central,OU=Client Mailboxes,DC=creativegroupinc,DC=com"

 }else{ $addn  =  "OU=Canada,OU=Client Mailboxes,DC=creativegroupinc,DC=com"

 }

 $ADUserProperties  = @{

#  Name =  "$FirstName $LastName"

 Path =  $addn

 SamAccountName =  $Alias

 UserPrincipalName = $emailaddr

 DisplayName = "$DispName"

 EmailAddress =  $emailaddr

 OtherAttributes = @{

 ProxyAddresses = $smtprox

 } 

 }

while ($true) {

 $currentuser  =  Get-ADUser  -Identity  $ADUserProperties.SamAccountName -ErrorAction  SilentlyContinue

 if ($currentuser.SamAccountName -eq $ADUserProperties.SamAccountName){

 Invoke-Command  -ComputerName  "DC-where-adsync-installed-here"  -ScriptBlock {Start-Service  -Name  ADSync}; Write-Host  "A User Name Requested already Exist: $Alias \- Please Fix and try again";Disconnect-ExchangeOnline;sleep  3;exit

 }

 else{

 Write-Host "Continue.." -ErrorAction SilentlyContinue;break

 }

 }

Invoke-Command  -ComputerName  "DC-where-adsync-installed-here"  -ArgumentList  $ADUserProperties  -ScriptBlock {

 param($ADUserProperties)

 $ADUser  =  New-ADUser  @ADUserProperties  -PassThru

}

$exsession  =  New-PSSession  -ConfigurationName  Microsoft.Exchange  -ConnectionUri  http://"on-prem-mail-srv-here"/PowerShell/  -Authentication  Kerberos

Import-PSSession  $exsession  -DisableNameChecking  -WarningAction  SilentlyContinue

$mailboxaddr  =  $ADUserProperties.SamAccountName

Invoke-Command  -ArgumentList  $mailboxaddr  -ScriptBlock {

param($mailboxaddr)

Enable-RemoteMailbox  -Shared  $mailboxaddr  -RemoteRoutingAddress  "$mailboxaddr@creativegroupinc2.mail.onmicrosoft.com"

}

Remove-PSSession  $exsession  -Confirm:$false

Invoke-Command  -ComputerName  "DC-where-adsync-installed-here"  -ScriptBlock {Start-Service  -Name  ADSync}

Invoke-Command  -ComputerName  "DC-where-adsync-installed-here"  -ScriptBlock {Start-ADSyncSyncCycle  -PolicyType  Initial}

while ($true) {

 $ADUser  =  Get-MsolUser  -UserPrincipalName  $emailaddr  -ErrorAction  SilentlyContinue

 if ($ADUser.UserPrincipalName -eq $ADUserProperties.EmailAddress){

 break

 }

 else{

 Start-Sleep  -Seconds  10;Write-warning  "Waiting on User Sync To Finish....!"

 }

 }

while ($true) {

 $EXMBOX = Get-mailbox -Identity $ADUserProperties.SamAccountName -ErrorAction SilentlyContinue

 if ($EXMBOX.Alias -eq $ADUserProperties.SamAccountName){

 break

 }

 else{

 Start-Sleep  -Seconds  10;Write-warning  "Waiting on Mailbox Sync To Finish....!"

 }

 }

Set-Mailbox  $ADUser.UserPrincipalName -MessageCopyForSentAsEnabled  $True

Set-Mailbox  $ADUser.UserPrincipalName -MessageCopyForSendOnBehalfEnabled  $True

foreach($mbm  in  $MboxMembers){

 $mbmu  =  Get-ADUser  -Filter  *  |  where-object{$_.Name -eq  $mbm} |  select  UserPrincipalName

 $mbmupn  =  $mbmu

 $upnname=$mbmupn.UserPrincipalName

 $upnname

 Add-MailboxPermission  -Identity  TestShare  -User  $upnname  -AccessRights  FullAccess

 }

Remove-Item  -Path  $PATH\$nurcsv

 }

}

Disconnect-ExchangeOnline  -Confirm:$false
```
