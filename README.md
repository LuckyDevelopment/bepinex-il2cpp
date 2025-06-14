1. Download DotNET and make sure it's downloaded.
2. Run ``dotnet new install BepInEx.Templates::2.0.0-be.4 --nuget-source https://nuget.bepinex.dev/v3/index.json`` in terminal.
3. In the terminal run ```dotnet new bep6plugin_unity_il2cpp -n MyFirstPlugin
dotnet restore MyFirstPlugin```
4. Your .csproj should include all nescessary items in the ``<ItemGroup>`` like UnityEngine, UnityEngine.CoreModule, 0Harmony, BepInEx.Unity.Il2CPP, BepInEx.PluginInfoProps, and any other .dll
5. Put all of the .dll files from ``unity-libs`` into a lib folder in the same directory as the .cs and .csproj folder so you can reference them.
6. Run ``dotnet build`` to build it.


## Example CSPROJ
```csproj
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net6.0</TargetFramework>
    <AssemblyName>MyFirstPlugin</AssemblyName>
    <Product>My first plugin</Product>
    <Version>1.0.0</Version>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
    <LangVersion>latest</LangVersion>
    <RestoreAdditionalProjectSources>
      https://api.nuget.org/v3/index.json;
      https://nuget.bepinex.dev/v3/index.json;
      https://nuget.samboy.dev/v3/index.json
    </RestoreAdditionalProjectSources>
    <RootNamespace>MyFirstPlugin</RootNamespace>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="BepInEx.Unity.IL2CPP" Version="6.0.0-be.*" IncludeAssets="compile" />
    <PackageReference Include="BepInEx.PluginInfoProps" Version="2.*" />
    

     <Reference Include="0Harmony">
      <HintPath>./lib/0Harmony.dll</HintPath>
      <Private>false</Private>
    </Reference>
     <Reference Include="AssemblyCSharp">
      <HintPath>./lib/Assembly-CSharp.dll</HintPath>
      <Private>false</Private>
    </Reference>
    <Reference Include="UnityEngine">
      <HintPath>./lib/UnityEngine.dll</HintPath>
      <Private>false</Private>
    </Reference>
    <Reference Include="UnityEngine.CoreModule">
      <HintPath>./lib/UnityEngine.CoreModule.dll</HintPath>
      <Private>false</Private>
    </Reference>
    <Reference Include="UnityEngine.IMGUIMODULE">
      <HintPath>./lib/UnityEngine.IMGUIModule.dll</HintPath>
      <Private>false</Private>
    </Reference>
  </ItemGroup>
</Project>
```
