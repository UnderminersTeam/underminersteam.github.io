---
title: Main Options JSON Specification
weight: 100
---

This page contains the specification for the main `project.json` file that is used in the project system.

The file can be modified outside of UndertaleModTool in order to use more technical or obscure features.

## Main JSON fields

| Field | Type | Description |
| ----- | ---- | ----------- |
| `Name` | `string` | Name of the project, purely for informational use. |
| `Flags` | `array` | Array of `string`s, representing project flags to be enabled. Flag names beginning with `_` can be used for any purpose (e.g. from CSX scripts), and all other flags are reserved. |
| `VerifyStrings` | `array` | Array of `string`s, representing strings that must exist in the source data file for project opening to be successful. |
| `AssetsDataFilePath` | [`PathList`](#pathlist) | If no data file is already loaded when opening a project, this will be used to find a source (and corresponding destination) data file to import assets to. |
| `ErrorOnWarnings` | `bool` | If `true` (default), data file save/load warnings will be escalated to errors. |
| `ExcludeDirectories` | `array` | Array of `string`s, representing root-level folder/directory names that will be excluded from asset importing. This is useful to store custom JSON files without errors, or anything non-project related. |
| `SubProjects` | `array` | Array of `string`s, representing relative paths to sub-project JSON (`project.json`) files. These sub-projects will be imported after pre-import scripts run, but before anything else. |
| `Patches` | `array` | Array of [`Patch`](#patch), representing file patches that should be applied (to external files, or even data files). This is done before the source data file is loaded, if it hasn't already been loaded. |
| `ExternalFiles` | `array` | Array of [`PathPair`](#pathpair), representing external data files that should be copied to the destination directory. |
| `FileCopies` | `array` | Array of [`FileOperation`](#fileoperation), representing files that should be copied. |
| `FileDeletes` | `array` | Array of [`FileOperation`](#fileoperation), representing files that should be deleted. |
| `PreImportScripts` | `array` | Array of `string`s, containing relative paths to CSX scripts to be executed prior to all import operations. |
| `PreAssetImportScripts` | `array` | Array of `string`s, containing relative paths to CSX scripts to be executed just prior to asset import operations. |
| `PostImportScripts` | `array` | Array of `string`s, containing relative paths to CSX scripts to be executed after all import operations. (Before saving to the destination data file.) |

## PathPair
`PathPair` is a flexible data type that represents a source and destination path, and has two forms:

### Source path only
When providing a `string`, it will be intepreted as both the source and destination path.

```json
"data.win"
```

### Source and destination paths
Using the following syntax as an example, a source and destination path pair can be used.

```json
{
    "Source": "data.win",
    "Destination": "data_another.win"
}
```

## PathList
`PathList` is a special data type that is flexible to several use cases. In its most complete form, it can be thought of as an `array` of [`PathPair`](#pathpair).

This is a "list" because it allows multiple fallback options, if needed to support multiple configurations or platforms.

Some examples of a valid `PathList` are:

### Empty
No paths are provided at all.

```json
null
```

### Single source path
A single source path is provided, which will be automatically treated as the same as the destination path.

```json
"data.win"
```

### Single source and destination path
A single source path is provided, along with is corresponding destination path, which can be different.

```json
{
    "Source": "data.win",
    "Destination": "data_another.win"
}
```

### Combinations of the above
All of the above path "pairs" can be combined into an array, which will be enumerated in order until a valid/existing source path is found (depending on the context).

```json
[
    "data.win",
    {
        "Source": "game.unx",
        "Destination": "subdirectory/game.unx"
    }
]
```

## Patch
`Patch` represents a single file to be patched when importing a project. It is a JSON object with the following fields:

| Field | Type | Description |
| ----- | ---- | ----------- |
| `PatchPath` | `string` | Relative path to the patch file, e.g. a BPS file. |
| `DataFilePath` | [`PathList`](#pathlist) | Path (or possible paths) to be patched using the specified patch file. |

## FileOperation
`FileOperation` represents a file operation to possibly be performed when importing a project. It is a JSON object with the following fields:

| Field | Type | Description |
| ----- | ---- | ----------- |
| `Paths` | [`PathList`](#pathlist) | Possible source/destination paths for the file operation, from which only one will be used. |
| `Required` | `bool` | Optional (default `true`). If `true`, and no valid source paths are found, an error will be raised. |

If `Required` is not needed, a [`PathList`](#pathlist) which does not begin with `{` can be used as a syntax shortcut.
