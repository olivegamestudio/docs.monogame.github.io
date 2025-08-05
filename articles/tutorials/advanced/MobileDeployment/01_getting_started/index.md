title: "01: Setting Up MonoGame for Android and iOS Development"
description: "Get started with MonoGame mobile development by setting up your development environment, tools, and SDKs for Android and iOS platforms."

# Getting Started and Overview

This tutorial extends the **MonoGame 2D Dungeon Slime tutorial** to mobile platforms. If you haven't completed the desktop tutorial yet, we recommend finishing it first as we'll be building directly on that foundation.

## What You'll Learn

By the end of this mobile tutorial series, you'll have:
- Ported the Dungeon Slime game to run on Android and iOS
- Implemented touch controls to replace mouse and keyboard input
- Set up cross-platform project architecture for code sharing
- Learned debugging techniques for mobile development
- Published your game to both Google Play and the App Store
- Created automated deployment workflows

The core approach focuses on **code reuse** - you'll learn how to share your game logic across platforms while adapting the input and deployment for mobile devices.

# Development Requirements

## Android Development

**Platform Support:** Android development can be accomplished on either Windows PC or Mac. However, ARM64 variants of Windows do not run the Android simulator well.

**Required Tools:**
- **Android Device Manager** - Used to set up simulators (accessible through Visual Studio)
- **Android SDK Manager** - Used to install the SDK platforms

## iOS Development

**Platform Requirement:** iOS development requires a Mac, whether you develop entirely on it or use the Pair to Mac option with Windows Visual Studio.

**Development Approach Options:**
- **Native Mac Development** (recommended): Develop directly on Mac using JetBrains Rider or Visual Studio Code
- **Windows + Pair to Mac**: Develop on Windows Visual Studio, pair to Mac for building and deployment

Since **Visual Studio for Mac** has been deprecated, [JetBrains Rider](https://www.jetbrains.com/rider/) is the currently recommended IDE for Mac development.

*Personal note: I found the native Mac development experience with Rider to be smoother for iOS work, though the Windows + Pair to Mac approach works well for teams preferring to stay in the Windows ecosystem.*

**Additional Requirements:**
- **Xcode** - Required for iOS development and deployment
- **Apple Developer Account** - Required for physical device deployment and App Store publishing ([enrollment link](https://developer.apple.com/programs/enroll/))

## Next Steps

Once your development environment is configured, we'll move on to setting up the cross-platform project structure and exploring how touch input works on mobile devices.