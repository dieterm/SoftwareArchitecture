# MSBuild

## Properties
```xml
<PropertyGroup>
    <MyVariableName>someValue</MyVariableName>
</PropertyGroup>
```
Usage:
```xml
$(MyVariableName)
```

## Items (=arrays)
Create a new item with name `InstallInclude` and add several files to it:
```xml
<ItemGroup>     
    <InstallInclude Include="**\*.ascx" Exclude="packages\**" />
    <InstallInclude Include="**\*.asmx" Exclude="packages\**" />
    <InstallInclude Include="**\*.css" Exclude="packages\**" />
    <InstallInclude Include="**\*.html" Exclude="packages\**" />
    <InstallInclude Include="**\*.htm" Exclude="packages\**" />
    <InstallInclude Include="**\*.resx" Exclude="packages\**" />
    <InstallInclude Include="**\*.aspx" Exclude="packages\**" />
    <InstallInclude Include="**\*.js" Exclude="packages\**" />
    <InstallInclude Include="**\*.txt"  Exclude="**\obj\**;**\_ReSharper*\**;packages\**;**\.git\**;" />
    <InstallInclude Include="**\images\**" Exclude="packages\**" />
</ItemGroup>
```

Add item to existing itemgroup `InstallInclude`:
```xml
<CreateItem Include="$(MSBuildProjectDirectory)\Package\**\*.*">
    <Output TaskParameter="Include" ItemName="InstallInclude" />
</CreateItem>
```

Usage:
```xml
@(InstallInclude)
```