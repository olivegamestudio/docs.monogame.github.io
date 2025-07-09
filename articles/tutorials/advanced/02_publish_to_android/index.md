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

- **Package Configuration**: Your app needs a unique identifier and proper versioning

- **Code Signing**: Android requires all apps to be digitally signed for security

- **Release Build**: Optimized builds that perform better on devices

- **Store Preparation**: Metadata, screenshots, and compliance with store policies

## Package Configuration

### The Package Name

Your package name serves as the unique identifier for your app on the Play Store. Once published, this cannot be changed, so choose carefully.

To set your package name:

- In your Android project, open the Properties panel.

- Navigate to the Android Manifest section.

- Set the Package name field to your desired identifier (e.g., **com.yourstudio.dungeonslime**)

- Ensure the name follows reverse domain notation.

## The Package Version

Android apps use two version identifiers:

Version Name: The version string users see (e.g., "1.0.0")
Version Code: An integer that increases with each release (e.g., 1, 2, 3...)

[!IMPORTANT]
Package names must be unique across the entire Play Store. Use a domain you control (like com.yourstudio.gamename) to avoid conflicts. The package name cannot be changed after publication.

Set both values in the same properties panel where you configured the package name.

[!TIP]
Use semantic versioning for your version name (Major.Minor.Patch) and increment the version code by 1 for each release, even if it's just a minor update.

In Visual Studio, there is a manifest editor for both editing of name and version:

![Package Name and Version](images/android_package_name.png)


## Editing the Android Manifest

For more advanced configuration, you may need to edit the AndroidManifest.xml file directly. This file contains important metadata about your app including permissions, supported features, and hardware requirements.

Common manifest configurations for games include:

- **Screen orientation**: Lock to landscape or portrait

- **Hardware features**: Declare required features like accelerometer

- **Permissions**: Request necessary permissions like internet access

- **Target SDK**: Specify the Android version you're targeting.

## Creating a Release Build

Development builds include debugging information and are not optimized for performance. Release builds are optimized, smaller, and ready for distribution.

### Using Visual Studio

To create a release build in Visual Studio:

- Change the build configuration from **Debug** to **Release** in the toolbar.
- Right-click your Android project in the Solution Explorer.
- Select **Archive** from the context menu.
- Visual Studio will build and package your app.

The option can also be found under the **Build** menu and **Archive** option.

![Archive](images/android_archive.png)

The archiving process compiles your code in release mode, packages all assets, and prepares the app for signing and distribution.

[!NOTE]
The archive process may take several minutes depending on your project size and computer performance. This is normal as the build system is performing optimizations.

## Distribution Options

After the archive completes, Visual Studio will present distribution options:

![Archive Options](images/android_archive_distribute.png)

The main distribution options are:

- **Ad Hoc**: For testing on specific devices
- **Google Play**: For Play Store submission
- **Save to Disk**: For manual distribution or further processing

## App Signing and Security

Understanding Android App Signing
Android requires all apps to be digitally signed before they can be installed. This signature:

Verifies the app's authenticity
Ensures the app hasn't been tampered with
Links the app to the developer's identity

You'll need a signing key (also called a keystore) to sign your app.

## Creating and Managing Signing Keys

### Importing an Existing Keystore

If you already have a keystore file, you can import it:

- In the signing dialog, click **Import Keystore**

- Browse to your keystore file (usually with .jks or .keystore extension)

- Enter the keystore password and key alias information

![Signing configuration dialog](images/android_archive_signing.png)

![Importing an existing keystore file](images/android_import_keystore.png)

# Google Play Store Submission

## Preparing for Submission

Once your app is signed and built, you're ready to submit to the Google Play Store. You'll need:

- A Google Play Console developer account

- Your signed APK or AAB file

- App metadata (description, screenshots, etc.)

- Compliance with Play Store policies

## Accessing Google Play Console

Visit the [Google Play Console](https://play.google.com/console/u/0/developers) to manage your app submissions:

# Releasing to store

Set the package name and version.

Editing the AndroidManifest.xml

# Build release configuration


Distribute option


Import the signing key


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
