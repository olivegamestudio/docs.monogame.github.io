
# Requirements

You will require a Mac with XCode installed.


# Packaging



# Publishing and Archiving

From terminal

```
cd DungeonSlime.iOS

dotnet build -f net8.0-ios -c Release -p:RuntimeIdentifier=ios-arm64

dotnet publish -f net8.0-ios -c Release -p:RuntimeIdentifier=ios-arm64 -p:ArchiveOnBuild=true
```

From Xcode, Window, Organizer menu.

Select the archive, and press the Distribute App button.

Pick the appropriate option and continue.

Upload will start.
