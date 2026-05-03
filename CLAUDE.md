# filemanager — Cutefish File Manager

## Purpose
Simple, clean file manager with desktop icon support, places sidebar, path bar, file operations, thumbnails, and MIME type handling.

## Build
```bash
cmake -B build -DCMAKE_INSTALL_PREFIX=/usr && cmake --build build && sudo cmake --install build
```

## Dependencies
- Qt6 (Core, DBus, Quick, LinguistTools)
- KDE Frameworks 6 (KF6KIO, KF6Solid, KF6WindowSystem, KF6Config, KF6XmlGui)

## Structure
- `main.cpp`, `application.cpp/h`, `window.cpp/h`, `dbusinterface.cpp/h` — core
- `model/foldermodel.cpp/h` — folder listing
- `model/placesmodel.cpp/h`, `model/placesitem.cpp/h` — places sidebar
- `model/pathbarmodel.cpp/h` — path bar
- `model/dirlister.cpp/h` — directory listing
- `model/positioner.cpp/h` — icon positioning
- `cio/cfilejob.cpp`, `cio/cfilesizejob.cpp` — file operations
- `dialogs/` — create folder, file properties, open with dialogs
- `widgets/` — rubber band selection, item view adapter
- `desktop/` — desktop icon view, settings, dock D-Bus interface
- `helper/` — date helper, path history, file launcher, keyboard search
- `mimetype/` — MIME app manager, XDG desktop file parsing
- `thumbnailer/` — thumbnail provider and cache
- `draganddrop/` — drag and drop support
- `qml/` — 13 QML files (main, FolderPage, SideBar, PathBar, FolderGridView, OptionsMenu, GlobalSettings, Dialogs, Controls, Desktop)
- `com.cutefish.FileManager.xml` — D-Bus adaptor

## Install Targets
- Binary → `${CMAKE_INSTALL_BINDIR}`
- Desktop file `cutefish-filemanager.desktop` → `/usr/share/applications/`
- Translations → `/usr/share/cutefish-filemanager/translations/`

## Qt5→Qt6 Migration Notes
- Qt5 → Qt6, KF5 → KF6
- `KIO::mkdir` → `<KIO/MkdirJob>`
- `isUndoAvailable()` API change
- `JobUiDelegate` created via factory
- `setShowHiddenFiles` API update

## Status
✅ Ported, built, installed, pushed (github.com/ali-soomro)
