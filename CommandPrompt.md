# Command Prompt

## Use parameters
```shell
%1
```

```shell
REM Create directory to store install zips
mkdir %1\InstallPackage

REM Copy all the modules to a shared folder
xcopy "%1\Trunk\modules\modulename\obj\Release\*.dll" "\\internal-server-name\some-shared-folder\bin\" /Y/R
xcopy "%1\Trunk\modules\modulename\obj\Release\*.pdb" "\\internal-server-name\some-shared-folder\bin\" /Y/R
xcopy "%1\Trunk\modules\modulename" "\\internal-server-name\some-shared-folder\Portals\_default\Skins\modulename\" /Y/R/E
```