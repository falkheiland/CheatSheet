# Powershell

## Error Handling

```powershell
Write-Host "StatusCode:" $_.Exception.Response.StatusCode.value__
Write-Host "StatusDescription:" $_.Exception.Response.StatusDescription
```

## Parameter

### Validation

Get Validators

```powershell
[psobject].Assembly.GetType('System.Management.Automation.TypeAccelerators')::Get | Sort-Object -Property Value
````

IP Address

```powershell
[ValidateScript({$_ -match [IPAddress]$_ })]
```

Not Null or Empty

```powershell
[ValidateNotNullOrEmpty()]
```

## Plaster

Create new Module

```powershell
Invoke-Plaster -TemplatePath C:\Path\To\PlasterTemplate -DestinationPath  C:\Path\To\NewModule -Verbose
```

## Modules

Find

```powershell
Find-Module -Name *remote*
```

Publish

```powershell
Publish-Module -Repository PSRepository -Path C:\Path\To\Module
```

Get

```powershell
Get-Module -Name Mappings -ListAvailable
```

Uninstall

```powershell
Uninstall-Module -Name ModuleName -Force
```

Install

```powershell
Install-Module -Name ModuleName -Repository RepositoryName -Scope AllUsers
```

## Objects

Add Property

```powershell
 $Coll = Get-Coll |
     Add-Member -MemberType NoteProperty -Name $PropertyName -Value $PropertyValue -PassThru
```

Avoid '+=' Operator

```powershell
$data1 = 1..10000 | Foreach-Object { $_ }
$data2 = foreach($element in (1..10000)) { $element }
```

## Help

```powershell
Get-Help -ShowWindow -Name Get-Process
```

```powershell
Get-Help -Name Get-Process -Detailed
```

```powershell
Get-Help -Name Get-Process -Examples
```

```powershell
(Get-Help -Name remote).where{$_.Category -eq 'Function'}
```

## Useful Functions

Provides a graphical interface to let you explore and navigate an object.

```powershell
Get-Process | Show-Object
```

## Useful Modules

PowerShellCookbook (Show-Object)