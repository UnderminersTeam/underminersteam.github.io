---
title: Getting Started
weight: 1
---

Before getting started with making a mod using the project system, you'll want to set up some folders:
- Source folder: where the original, vanilla/unmodified game is
- Destination folder: where the modded game will go
- Project folder: where mod assets will be exported to, and reimported from

It's recommended to copy all game files from the "source folder" to the "destination folder," and the "project folder" can start out empty.
**It is also recommended that each of these three folders are located separately.**

## Creating a Project

Creating a project is most easily done from within UndertaleModTool:
1) `Project` -> `New project`
2) Select the source data file (e.g. `data.win`, from the "source folder")
3) Name your mod project (can be anything)
4) Select the "project folder" (should be empty)
5) Select the destination data file (e.g. `data.win`, from the "destination folder")

Then you're good to get started!

## Basic Usage

### Modifying assets
When a project is open in UndertaleModTool, you can edit assets as you normally would. When making any changes, you should verify that "Marked for export" is checked off in the bottom-right corner of the tool, as otherwise your changes will not be saved to the project.

### Playing (or testing) the mod
To simply test the mod, the Temp Run feature of UndertaleModTool will work, which is bound to F5 by default.

To permanently export the mod to be played, `File` -> `Save` will work. You likely want to say "yes" on the dialog box that may appear, which allows the project to be fully installed, including external data files, etc.

### Saving the project
To save modified assets (exporting them to the "project folder"), simply use `Project` -> `Save`. The tool should generally warn you if you forget to do this before closing, though.

### Viewing unexported assets
You can also go to `Project` -> `View unexported assets` to see which assets currently need to be exported/saved to the project. Assets can be dragged into this window, too, for quickly exporting certain assets.

## Advanced Usage

More advanced usage of the project system typically requires editing of JSON files (or assets in general) outside of UndertaleModTool.

Links to documentation of those files can be found [here](../what-is-it/#documentation).
