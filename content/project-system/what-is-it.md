---
title: What is it?
weight: 0
---

UndertaleModTool's project system is designed to be a more modern way of making mods.

Instead of modding a single data file (and hoping it doesn't get corrupted), the project system allows you to export all assets you've modified to a folder, which can then be re-imported whenever opening the project again.

This provides several benefits:
- The project folder of a mod can be tracked (and backed up) by version control, such as Git.
- Collaboration amongst multiple developers becomes much easier. (Git can be used, again.)
- GML code edits can be preserved in plaintext, rather than always being re-decompiled. Comments work! 
- File corruption isn't quite as disastrous.
- Modded assets can be edited outside of UndertaleModTool, in JSON format (or image/sound formats).
- If you're lucky, mods can be compatible across multiple game versions.

Want to get started? [See the basic setup instructions here](../getting-started/).

## Supported & Missing Features

The project system, as of writing, is currently not feature-complete.

Supported features currently are:
- Exporting and reimporting these assets:
    * Code (GML VM)
    * Game objects
    * Script assets
    * Rooms
    * Sounds
    * Backgrounds (or tilesets)
    * Sprites
    * Sequences
    * Animation curves
    * Fonts
    * Paths
    * Shaders
- Automatic marking of most asset types to be exported when making any changes in the GUI, or when using a built-in importer script.
- Ability to copy assets between projects (manually, outside of UndertaleModTool) to easily port assets between mods and games.
- Ability to edit certain General Info properties, via manual JSON editing.
- Customizing the source (asset) data file path.
- Excluding certain folders (directories) from being imported as assets, if you need to store other JSON files.
    * System folders, hidden folders, and directories beginning with `.` at the root of the project will be ignored by default.
- Sub-projects, to apply mods to multiple data files (e.g. Deltarune chapters) at the same time.
- BPS file patching, to support legacy mods and to support modifying binary data easily.
- External data file/directory copying and deleting.
- Custom CSX scripts that can be run in multiple stages:
    * Before anything is imported
    * Before assets are imported
    * After everything is imported
- A simple file backup system when installing a mod from a project.
- Ability to recompile all project-touched GML code when saving, to prevent newly-added asset name issues.
- Game version detection and verification when installing a project, via manual JSON editing.
- CLI option to build/install a project, so it can be automated.
- Custom sprite import settings, manually defined in JSON.

Unsupported (but desired/planned) features currently are:
- Remaning CLI options to manage projects.
- Extension asset support.
- More robust code modification, that can be more resilient across game versions:
    * Preprocessor directives (e.g. insert before/after, find and replace)
- Ability to export and import assets outside of a project, but using the same format.
- Ability to duplicate assets, reusing internal project system logic.
- GUI button to reload the entire data file and project in one click.
- Custom texture group support (and their associated settings).
- Custom audio group support.
- Way to mostly automate porting legacy mods to be usable in the project system.

## Documentation

As of writing, documentation on the project system is still expanding.

As for file format/JSON documentation:
- The main project JSON file (`project.json`) has a basic specification [here](../main-options-spec/).
- The optional `general-info-options.json` file has a specification [here](../general-info-spec/).

For a complete view of everything, the C# source code is commented and available within `UndertaleModLib`'s `Project` namespace. [That can be viewed on GitHub here.](https://github.com/UnderminersTeam/UndertaleModTool/tree/master/UndertaleModLib/Project)
