# Godot Version Manager

Godot Version Manager (gdvm) is a tool designed to simplify the installation, management, and switching between different versions of the Godot Engine.

Whether you're working on multiple projects or need to test features across various Godot versions, you'll never need to manually fuss with Godot installations again.

## Installation

Install on \*nix systems (including MacOS):

```bash
curl -sSL https://raw.githubusercontent.com/adalinesimonian/gdvm/main/scripts/install.sh | bash
```

Install on Windows:

```powershell
powershell -NoProfile -Command "(iwr -useb 'https://raw.githubusercontent.com/adalinesimonian/gdvm/main/scripts/install.ps1').Content | iex"
```

### Supported Platforms

- Windows (64-bit, 32-bit, and 64-bit ARM)
- macOS (64-bit Intel and Apple Silicon)
- Linux (64-bit, 32-bit, and 64-bit ARM)

## Usage

Once installed, you can use the `gdvm` command to manage your Godot installations. Here are some common commands:

```bash
gdvm use stable              # Sets the system-wide default version of Godot to
                             # the latest stable version

gdvm pin stable --csharp     # Pins the default version for the current folder
                             # to the latest stable version with C# support,
                             # using a .gdvmrc file in the current folder
```

> [!TIP]
> If you pin or use a global system version, you can associate `.godot` files in your OS with `~/.gdvm/bin/godot.exe` to automatically use either the system-wide version of Godot or the pinned version for the project directory to open that project file.
>
> gdvm will also try to detect the Godot version from the `project.godot` file and use the appropriate version if it's installed, for projects that don't have a pinned version.

```bash
gdvm run                     # Runs the default version of Godot for the current
                             # folder or the system-wide default version if the
                             # current folder is not pinned
godot                        # Equivalent to `gdvm run`
godot_console                # (Windows only) Same as `gdvm run`, but with the
                             # console window open
gdvm run 3.5 --csharp        # Runs Godot version 3.5 with C# support
gdvm remove 3.5              # Removes Godot version 3.5 without C# support
gdvm list                    # Lists all installed Godot versions
gdvm search 4                # Searches for all 4.x versions of Godot
gdvm upgrade                 # Upgrades gdvm to the latest version
```

> [!NOTE]
> If you encounter GitHub API rate limit errors, you may need to wait or use a personal access token to increase your limit. To use a personal access token:
>
> 1. [Create a fine-grained personal access token](https://github.com/settings/personal-access-tokens) with access to public repositories.
> 2. Run `gdvm config set github.token` and enter your token when prompted. You can also use the `GITHUB_TOKEN` environment variable to set the token, useful for CI/CD pipelines.
>
> Note that running `gdvm config set github.token` will store the token in plain text in the `~/.gdvm/config.toml` file, so make sure to keep it secure.

For more information, run

```bash
gdvm --help
```

## Contributing

Please see [Contributing](CONTRIBUTING.md) for guidelines.

## Code of Conduct

Please see [Code of Conduct](CODE_OF_CONDUCT.md) for details.

## Licence

[ISC](LICENCE)
