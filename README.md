# Powershell

- [Error Handling](#error-handling)
  - [Exception Response](#exception-response)
- [Credential](#credential)
- [Parameter](#parameter)
  - [Validation](#validation)
  - [Accept Arrays](#accept-arrays)
- [Plaster](#plaster)
- [Modules](#modules)
- [String](#string)
  - [Concatenating](#concatenating)
  - [extract a part of the string](#extract-a-part-of-the-string)
- [Here String](#here-string)
  - [Create](#create)
  - [Join](#join)
- [Objects](#objects)
  - [Write-Output vs Return](#write-output-vs-return)
  - ['+=' Operator](#-operator)
  - [Property](#property)
  - [OutVariable](#outvariable)
- [Hashtable](#hashtable)
  - [Ordered](#ordered)
  - [Add items](#add-items)
- [Help](#help)
- [Useful Functions](#useful-functions)
- [Useful Modules](#useful-modules)
- [Statements](#statements)
  - [#Requires](#requires)
- [CmdletBinding](#cmdletbinding)
  - [DefaultParameterSetName](#defaultparametersetname)
  - [SupportsShouldProcess](#supportsshouldprocess)
  - [ConfirmImpact](#confirmimpact)
- [Formatting](#formatting)
  - [Line break](#line-break)
- [Regular expressions, regex](#regular-expressions-regex)
  - [Named matches (capture group name)](#named-matches-capture-group-name)
  - [.net Regex](#net-regex)
- [Diverse](#diverse)
  - [remove UTF8 BOM](#remove-utf8-bom)
  - [SQL NULL value](#sql-null-value)
  - [DateTime](#datetime)

## Error Handling

```powershell
foreach ($Item in $ItemColl)
{
  try
  {
    $Item = Get-Item -ErrorAction Stop
  }
  catch
  {
    $Item = 'Error'
  }
  finally
  {
    Write-Output $Item
  }
}
```

## Credential

Save credential

```powershell
Get-Credential | Export-Clixml -Path ('{0}\user@hostname.cred' -f ${env:\userprofile})
```

Load credential

```powershell
$Credential = Import-Clixml -Path ('{0}\user@hostname.cred' -f ${env:\userprofile})
```

### Exception Response

Invoke-RestMethod

```powershell
Write-Output "StatusCode:" $_.Exception.Response.StatusCode.value__
Write-Output "StatusDescription:" $_.Exception.Response.StatusDescription
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

### Accept Arrays

```powershell
[string[]]
$MultipleItems = 'apple', 'orange', 'banana'
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

Find Path

```powershell
(Get-Module -Name ((Get-Command Get-Process).ModuleName) | Select-Object -Property *).ModuleBase
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

## String

### Concatenating

join

```powershell
-join('aaa', 'bbb')
```

f operator

```powershell
'{0}{1}' -f 'aaa', 'bbb'
```

### extract a part of the string

substring

```powershell
$FirstTwoChars = ('abcdefg').Substring(0, 2)
```

Left and right part from delimiter

```powershell
$Name = 'aaaaaaaaaa;bbbbbbbbb'
$Pos = $Name.IndexOf(';')
$LeftPart = $Name.Substring(0, $Pos)
$RightPart = $Name.Substring($Pos + 1)
```

## Here String

### Create

```powershell
$HereString = @'
     sadsada
   asdsadas
dasssd
 fsf  ff
'@
```

### Join

```powershell
$HereStringA = @"
asdasd
dgfg
    dfg
"@
$HereStringB = @'
asdfsdassdfdfd
        ds gfdg
  dfgd
'@
$HereStringA, $HereStringB -join "`n"
```

## Objects

### Write-Output vs Return

Return | Write-Output
-------|-------------
only $Variable | all Outputs

### '+=' Operator

Avoid

```powershell
$data1 = 1..10000 | Foreach-Object { $_ }
$data2 = foreach($element in (1..10000)) { $element }
```

Use

* if first collect subroutine

```powershell
$Obj = @()
foreach ($item in $items)
{
  $Obj += $item
}
Write-Output $Obj
```

### Property

Add

```powershell
 $Coll = Get-Coll |
     Add-Member -MemberType NoteProperty -Name $PropertyName -Value $PropertyValue -PassThru
```

Rename (Avoid Alias)

```powershell
Get-ADComputer -Filter * | Select-Object -Property @{name = 'Computername'; expression = {$_.name}}
```

Order by multiple

```powershell
Get-Service | Sort-Object -Property @{
  Expression = "Status"; Descending = $True
}, @{
    Expression = "DisplayName"; Descending = $False
  }
```

Calculated

```powershell
Get-ChildItem -Path $Path -Filter '*.txt' |
  Sort-Object -Property @{
      Expression = {$_.LastWriteTime - $_.CreationTime}; Ascending = $False
      } |
  Format-Table LastWriteTime, CreationTime
```

### OutVariable

```powershell
$Null = Get-Service -OutVariable GetService |
  Sort-Object -Property Status -Descending -OutVariable GetServiceByStatus |
  Format-Table -AutoSize -OutVariable GetServiceByStatusAutosize

$GetService
$GetServiceByStatus
$GetServiceByStatusAutosize
```

## Hashtable

### Ordered

```powershell
$OrderedHashTable = [ordered]@{
  a = 1
  b = 2
  c = 3
  d = 4
}
```

### Add items

```powershell
$HashTable = @{}
Get-ChildItem -Path $env:windir -Filter *.exe | ForEach-Object {

  $HashTable.Add($_.Name.ToString() , $_.Length.ToString())
}
$HashTable
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

quick replacement for Out-Gridview, Excel has to be installed

```powershell
Get-Process | Export-Excel -Now -WarningAction SilentlyContinue
```

## Useful Modules

* PowerShellCookbook (Show-Object)
* ImportExcel

## Statements

### #Requires

* #Requires -Version N[.n]
* #Requires -PSEdition [ Core | Desktop ]
* #Requires –PSSnapin PSSnapin-Name [-Version N[.n]]
* #Requires -Modules { Module-Name | Hashtable }
* #Requires –ShellId ShellId
* #Requires -RunAsAdministrator

## CmdletBinding

* advanced function

```powershell
[CmdletBinding(DefaultParameterSetName = 'Set1', SupportsShouldProcess = $true, ConfirmImpact = 'Medium')]
```

### DefaultParameterSetName

### SupportsShouldProcess

WhatIf, Comfirm Support

```powershell
if ($PSCmdlet.ShouldProcess('ID: {0}' -f $ID))
{
  Remove-Something -ID $ID
}
```

### ConfirmImpact

Whenever the ConfirmImpact is equal or higher than the $ConfirmPreference (Default 'High'), a confirmation is required.

## Formatting

### Line break

Line too long

```powershell
Get-WmiObject -Class 'Win32_LogicalDisk' -Filter 'DriveType=3' -Computername 'localhost'
```

Backticks

* hard to read
* trailing spaces break code

```powershell
Get-WmiObject -Class 'Win32_LogicalDisk' `
-Filter 'DriveType=3' `
-ComputerName 'localhost'
```

Splatting

```powershell
$GetWmiObjectParams = @{
  Class        = 'Win32_LogicalDisk'
  Filter       = 'DriveType=3'
  Computername = 'localhost'
}
Get-WmiObject @GetWmiObjectParams
```

Other

line break after almost any comma, pipe character, or semicolon

## Regular expressions, regex

[Powershell: The many ways to use regex](https://kevinmarquette.github.io/2017-07-31-Powershell-regex-regular-expression/)

### Named matches (capture group name)

```powershell
$Text = '192.168.0.1 computer01.domain.com 001122334455'
$Pattern = '^(?<IPv4>\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})\s+(?<Computername>(\w|\d|\.)+)\s+(?<MAC>\d{12})'
if ($Text -match $Pattern)
{
  $matches
}
```

Part of an OU

```powershell
$Text = 'cn=JSmith,ou=Management,ou=users,ou=London,dc=company,dc=com'
$Pattern = '^.+ou=(?<Location>(\w|\d|\s)+)(?!.+ou){1}'
$Location = ([regex]::match($Text, $Pattern).captures.groups).Where{$_.Name -eq 'Location'}.Value
```

Filename and Path

```powershell
$Text = 'C:\Temp\Subdir01\Test.txt'
$Pattern = '(?<Path>.+)\\(?<Filename>(?:.(?!\\))+$)'
$Filename = ([regex]::match($Text, $Pattern).captures.groups).Where{$_.Name -eq 'Filename'}.Value
$Path = ([regex]::match($Text, $Pattern).captures.groups).Where{$_.Name -eq 'Path'}.Value
```

create object

```powershell
$TextColl = '192.168.0.1 computer01.domain.com 001122334455', '192.168.0.2 computer02.domain.com 001122334466'
$Pattern = '^(?<IPv4>\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})\s+(?<Computername>(\w|\d|\.)+)\s+(?<MAC>\d{12})'
$Result = foreach ($Text in $TextColl)
{
  if ($Text -match $Pattern)
  {
    New-Object -TypeName PsObject -Property $matches
  }
}
$Result
```

### .net Regex

get methods

```powershell
[regex]::new($pattern) | Get-Member
```

match string

```powershell
[regex]::match($string,"^(\w{3})(\w{2,3})-.*$")
```

## Diverse

### remove UTF8 BOM

```powershell
[System.IO.File]::WriteAllLines($FilePath, (Get-Content -Path $FilePath))
```

```powershell
(Get-Content -Path $FilePath) -replace '\xEF\xBB\xBF', '' |
  Set-Content -Path $FilePath
```

### SQL NULL value

```powershell
if ($Property.Value -is [System.DBNull])
{
  $Value = $Null
}
```

### DateTime

**ISO 8601:**

```powershell
(Get-Date).ToString('s')
```

``` console
2018-09-14T13:08:14
```
