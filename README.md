# renpy-mac-stubs

Pre-built minimal RenPy Mac `.app` bundles ("stubs") for running Windows-only RenPy games on macOS.

## The problem

Many RenPy games are released Windows-only. To run them on Mac you need a Mac build of the same RenPy version. Finding exact versions can be hard.

## The solution

Download the stub for your game's RenPy version, replace its `game/` folder with a symlink to your game's `game/` folder.

## Usage

```bash
# Download stub for your version (requires gh cli)
gh release download v7.4.11 --repo YOUR_USERNAME/renpy-mac-stubs --pattern "*.zip"

# Unzip
unzip renpy-7.4.11-mac-stub.zip

# Replace game/ with symlink to your Windows game's game/ folder
rm -rf "renpy-stub-7.4.11-mac/renpy-stub.app/Contents/Resources/autorun/game"
ln -s "/path/to/your/windows-game/game" \
      "renpy-stub-7.4.11-mac/renpy-stub.app/Contents/Resources/autorun/game"

# Remove quarantine (unsigned app)
xattr -cr "renpy-stub-7.4.11-mac/renpy-stub.app"

# Launch
open "renpy-stub-7.4.11-mac/renpy-stub.app"
```

> **Note:** The exact path inside the `.app` may vary between RenPy versions. Check the structure after unzipping if the above path doesn't work.

## Building

- **Single version:** Actions → "Build Single Version" → Run workflow → enter version
- **All versions:** Actions → "Build All Versions" → Run workflow
