---
title: "XX: Deploying to Android"
description: "Learn how to prepare, build, and deploy your MonoGame project to the Google Play Store for Android devices."
Getting your MonoGame project ready for Android devices and the Google Play Store involves several important steps. Think of this process like preparing a product for retail sale - you need proper packaging, certification, and distribution channels to reach your audience.
---

In this chapter you will:

- Configure your Android project for release deployment
- Set up proper package naming and versioning
- Create and manage signing keys for app authentication
- Prepare your app for Google Play Store submission
- Understand the deployment workflow from development to distribution

# Understanding Android App Deployment

Before diving into the technical steps, it's important to understand what happens when you deploy an Android app. Unlike running your game in development mode, releasing to the Play Store requires:

Package Configuration: Your app needs a unique identifier and proper versioning
Code Signing: Android requires all apps to be digitally signed for security
Release Build: Optimized builds that perform better on devices
Store Preparation: Metadata, screenshots, and compliance with store policies


# Release to store

Set the package name and version.

![iOS Simulator](images/android_package_name.png)

Editing the AndroidManifest.xml

# Build release configuration

From Visual Studio - Build... Archive

![iOS Simulator](images/android_archive.png)

Distribute option

![iOS Simulator](images/android_archive_distribute.png)

Import the signing key

![iOS Simulator](images/android_archive_signing.png)

![iOS Simulator](images/android_import_keystore.png)

Select location to mykeystore.jks

https://play.google.com/console/u/0/developers

![iOS Simulator](images/android_release.png)





```csharp
    <SupportedOSPlatformVersion>23</SupportedOSPlatformVersion>
```

```csharp
    <ApplicationId>com.companyname.DungeonSlime.Android</ApplicationId>
    <ApplicationVersion>1</ApplicationVersion>
    <ApplicationDisplayVersion>1.0</ApplicationDisplayVersion>
```

```csharp
    <PackageReference Include="MonoGame.Framework.Android" Version="3.8.*" />
```

## Full csproj file

```csharp
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>net8.0-android</TargetFramework>
    <SupportedOSPlatformVersion>23</SupportedOSPlatformVersion>
    <OutputType>Exe</OutputType>
    <ApplicationId>com.companyname.DungeonSlime.Android</ApplicationId>
    <ApplicationVersion>1</ApplicationVersion>
    <ApplicationDisplayVersion>1.0</ApplicationDisplayVersion>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="MonoGame.Content.Builder.Task" Version="3.8.*" />
    <PackageReference Include="MonoGame.Framework.Android" Version="3.8.*" />
  </ItemGroup>
  <Target Name="RestoreDotnetTools" BeforeTargets="CollectPackageReferences">
    <Message Text="Restoring dotnet tools (this might take a while depending on your internet speed and should only happen upon building your project for the first time, or after upgrading MonoGame, or clearing your nuget cache)" Importance="High" />
    <Exec Command="dotnet tool restore" />
  </Target>
</Project>
```
