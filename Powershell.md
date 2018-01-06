# Powershell

## Reading commandline arguments
```powershell
$destination = $args[0]
```

## Map shared folder using credentials
```powershell
net use \\servername-or-ipadress\sharedfoldername "mySecretPassword" /USER:"myUserName"
```

## Create directory to store install zips
```powershell
New-Item -ItemType Directory -Force -Path $destination\InstallPackage
```

## Copy all the modules to a shared folder
```powershell
copy-item -Path $destination\Trunk\modules\mymodule\obj\Release\*.dll -Destination \\internal-server-name\some-shared-folder\bin\ -force -recurse -verbose
copy-item -Path "$destination\Trunk\modules\mymodule\obj\Release\*.dll" -Destination \\internal-server-name\some-shared-folder\bin\ -force -recurse -verbose
```

## Create Zip file from foldercontent (using .net)
See https://msdn.microsoft.com/en-us/library/hh485707(v=vs.110).aspx
```powershell
$sourceFolder = "$source\InstallPackage"

$destinationZip = "$destination\InstallPackage.zip"

If(Test-path $destinationZip) {Remove-item $destinationZip}

Add-Type -assembly "system.io.compression.filesystem"

[io.compression.zipfile]::CreateFromDirectory($sourceFolder, $destinationZip) 
```

## Unzip archive to folder (using .net)
See https://msdn.microsoft.com/en-us/library/hh485723(v=vs.110).aspx
```powershell
$sourceZip = "$source\InstallPackage.zip"

$destinationFolder = "$destination\InstallPackage"

Add-Type -assembly "system.io.compression.filesystem"

[io.compression.zipfile]::ExtractToDirectory($ourceZip, $destinationFolder) 
```