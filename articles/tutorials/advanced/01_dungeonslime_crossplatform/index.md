title: "01: Setting Up Cross-Platform Projects"
description: "Learn how to convert a Windows-only MonoGame project to support iOS and Android platforms, creating a unified codebase for multi-platform deployment."

In this chapter you will:

- Convert a Windows-only MonoGame project to support multiple platforms.

- Understand the project structure for multi-platform games.

# Converting the Dungeon Slime Project

The Dungeon Slime game from the [Building 2D games](..\building_2d_games) tutorial has been updated to demonstrate cross-platform support.

This conversion serves as a practical example of the steps needed to make any MonoGame project work across multiple platforms.

# Project Structure Overview

When converted to cross-platform, your solution structure will look like this:

![Cross Platform Projects](images\crossplatform_projects.png)

## DungeonSlime.Common - Sharing logic

The common project that contains the logic.

```csharp
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFrameworks>net8.0;net8.0-ios;net8.0-android</TargetFrameworks>
    </PropertyGroup>
    <ItemGroup>
        <PackageReference Include="Gum.MonoGame" Version="2025.6.26.1" />
    </ItemGroup>
    <ItemGroup Condition="'$(TargetFramework)'=='net8.0-ios'">
        <PackageReference Include="MonoGame.Framework.iOS" Version="3.8.4" />
    </ItemGroup>
    <ItemGroup Condition="'$(TargetFramework)'=='net8.0-android'">
        <PackageReference Include="MonoGame.Framework.Android" Version="3.8.4" />
    </ItemGroup>
    <ItemGroup Condition="'$(TargetFramework)'=='net8.0'">
        <PackageReference Include="MonoGame.Framework.DesktopGL" Version="3.8.4" />
    </ItemGroup>
    <ItemGroup>
      <ProjectReference Include="..\MonoGameLibrary\MonoGameLibrary.csproj" />
    </ItemGroup>
</Project>
```

## Moved game code from windows version to the common project

Moved the logic classes into the common project. The iOS, Android and Windows projects become effectively shells.

Removed game class from android and ios project.

This structure includes:

**Shared Code**: Your main game logic that works across all platforms. This can be found in the **DungeonSlime.Common** project.

**Platform-Specific Projects**: Individual projects for Windows, Android, and iOS. These are named **DungeonSlime.Windows**, **DungeonSlime.Android** and **DungeonSlime.iOS**.

## Third-Party Libraries updated

Many third-party libraries also need to be updated for cross-platform compatibility.

For example, the Gum UI library:

```xml
<PackageReference Include="Gum.MonoGame" Version="2025.6.26.1" />
```
