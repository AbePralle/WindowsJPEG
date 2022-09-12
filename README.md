# Windows Media Libraries
This repo contains Visual Studio 2022 projects (solutions) to build static JPEG, PNG, and ZLIB libraries for Windows.

# Current Versions
Library    | Version  | Solution Filepath                          | Product
-----------|----------|--------------------------------------------|-------------
JPEG       | 9d       | Projects\jpeg\libjpeg.sln                  | Libraries\jpeg
PNG        | 1.6.37   | Projects\png\projects\vstudio\vstudio.sln  | Libraries\lpng
ZLIB       | 1.2.11   | (Built as part of PNG project)             | Libraries\zlib

# Updating and Building

## JPEG
  1. Download the latest Windows release from [https://sourceforge.net/projects/libpng/files/](https://sourceforge.net/projects/libpng/files/) and unzip it into `Libraries\jpeg`.
  2. Open `Projects\jpeg\libjpeg.sln` in Visual Studio 2022+.
  3. Set the solution configuration to `Release` and then select `Build > Build Solution`.
  4. Update the JPEG version in `Versions.json`.
  5. Run `rogo` to copy the build product and headers to the `Libraries` folder.

## PNG
1. Download latest release from [https://sourceforge.net/projects/libpng/files/](https://sourceforge.net/projects/libpng/files/) and replace `Projects\png` with the new version.
2. Open `Projects\png\projects\vstudio\vstudio.sln` in Visual Studio 2022+.
3. Set the solution configuration to `Release Library`.
4. Select `Build > Build Solution` from the menu.
    - If the build fails due to build tools v142 not being found, search and replace `<PlatformToolset>v142` with `<PlatformToolset>v143` (using [ReID](https://github.com/AbePralle/ReID): `reid -e "<PlatformToolset>v142" "<PlatformToolset>v143"` from the `WindowsMediaLibraries\Projects\` folder).
    - If the build fails due to any warnings being treated as errors, list the warning numbers in `Properties > C/C++ > Advanced > Disable Specific Warnings`.
5. Run `rogo` to copy the build product and headers to the `Libraries` folder.

## ZLib
1. Download latest release from https://www.zlib.net .
2. Delete old `Projects\zlib` and rename downloaded `zlib-<version>` to `Projects\zlib`.
3. `zlib.lib` is produced by building the PNG project.
