# Black Atom for [PLATFORM_NAME]

> Elegant, cohesive themes for [PLATFORM_NAME] by Black Atom Industries

## What is a Black Atom Adapter?

This repository is a **[PLATFORM_NAME] adapter** for the Black Atom theme ecosystem. In the Black Atom architecture:

- The [core repository](https://github.com/black-atom-industries/core) is the single source of truth for all theme definitions
- Each adapter implements these themes for a specific platform ([PLATFORM_NAME], Neovim, terminals, etc.)
- The adapter uses templates to transform core theme definitions into platform-specific files

This modular approach ensures consistent colors and styling across all supported platforms while allowing for platform-specific optimizations.

## Available Themes

Black Atom includes multiple theme collections, each with dark and light variants:

| Collection    | Description                   |
| ------------- | ----------------------------- |
| **Default**   | Core Black Atom themes        |
| **JPN**       | Japanese-inspired themes      |
| **MNML**      | Minimalist accent themes      |
| **Stations**  | Space station-inspired themes |
| **Terra**     | Earth season-inspired themes  |

## Installation

<!-- REPLACE WITH PLATFORM-SPECIFIC INSTALLATION INSTRUCTIONS -->

### Prerequisites

- [PLATFORM_NAME] application
- [Black Atom Core](https://github.com/black-atom-industries/core) (for generating themes)

### Setup

1. Clone this repository:

```bash
git clone https://github.com/black-atom-industries/[PLATFORM_NAME].git
cd [PLATFORM_NAME]
```

2. Generate theme files using Black Atom Core:

```bash
black-atom-core generate
```

3. [PLATFORM_SPECIFIC_INSTALLATION_STEPS]

## Usage

<!-- REPLACE WITH PLATFORM-SPECIFIC USAGE INSTRUCTIONS -->

[PLATFORM_SPECIFIC_USAGE_INSTRUCTIONS]

## Development

This repository uses the Black Atom adapter pattern. Theme files are generated from templates using the core CLI.

### Installing Black Atom Core CLI

To generate themes, you need the Black Atom Core CLI installed:

```bash
# Clone and enter the core repository
git clone https://github.com/black-atom-industries/core.git
cd core

# Compile and install the CLI
deno task cli:compile
deno task cli:install
```

This installs the `black-atom-core` binary to `/usr/local/bin`.

### Creating Templates

Templates use the Eta template engine syntax to access theme properties:

```
<%= theme.ui.bg.default %>   <!-- Access a UI background color -->
<%= theme.meta.label %>      <!-- Access the theme name -->
<%= theme.palette.red %>     <!-- Access a palette color -->
```

**Important**: Never access `theme.primaries` directly in templates. Use `theme.ui`, `theme.syntax`, or `theme.palette` instead.

### Repository Structure

```
.
├── LICENSE                   # MIT license
├── README.md                 # This documentation
├── EXAMPLES.md               # Example templates in different formats
├── black-atom-adapter.json   # Adapter configuration file
└── themes/                   # Template directory
    ├── default/              # Default collection templates
    │   └── collection.template.[ext]
    ├── jpn/                  # JPN collection templates
    │   └── collection.template.[ext]
    ├── mnml/                 # MNML collection templates
    │   └── collection.template.[ext]
    ├── stations/             # Stations collection templates
    │   └── collection.template.[ext]
    └── terra/                # Terra collection templates
        └── collection.template.[ext]
```

### Setup Steps for New Adapters

1. **Update README.md** - Replace placeholders with platform-specific information
2. **Edit black-atom-adapter.json** - Configure collection-based templates
3. **Create collection templates** - Create `.template.{ext}` files for each collection
4. **Test your adapter** - Run `black-atom-core generate` to generate theme files

## Template Formats

Templates can be created in **any format** that your platform requires:

- **JSON**: For editors like VS Code, Zed
- **Lua**: For Neovim, Hammerspoon
- **CSS**: For web-based platforms
- **CONF**: For terminal emulators like Ghostty
- **YAML/TOML**: For various configuration formats

The only requirement is that template files follow the naming convention `.template.{ext}` and use Eta syntax for variable interpolation.

## Creating Templates

Templates use the Eta template engine syntax to access theme properties:

```
<%= theme.ui.bg.default %>   <!-- Access a UI background color -->
<%= theme.meta.label %>      <!-- Access the theme name -->
<%= theme.palette.red %>     <!-- Access a palette color -->
```

## Available Theme Properties

Your templates can access the following theme properties:

- `theme.meta` - Theme metadata (name, collection, appearance)
- `theme.palette` - Standard color palette (red, green, blue, etc.)
- `theme.ui` - UI colors (backgrounds, foregrounds, etc.)
- `theme.syntax` - Syntax highlighting colors

**IMPORTANT**: Never access `theme.primaries` directly in templates.

## Adapter Configuration

The `black-atom-adapter.json` file uses a collection-based approach to map templates to themes:

```json
{
  "collections": {
    "stations": {
      "template": "./themes/stations/collection.template.json",
      "themes": [
        "black-atom-stations-engineering",
        "black-atom-stations-operations",
        "black-atom-stations-medical",
        "black-atom-stations-research"
      ]
    },
    "jpn": {
      "template": "./themes/jpn/collection.template.json",
      "themes": [
        "black-atom-jpn-koyo-yoru",
        "black-atom-jpn-koyo-hiru",
        "black-atom-jpn-tsuki-yoru",
        "black-atom-jpn-murasaki-yoru"
      ]
    }
  }
}
```

This approach offers several advantages:

- **Reduced duplication**: One template file per collection instead of per theme
- **Better organization**: Themes are grouped by their collection
- **Easier maintenance**: When you need to update a template, you only need to modify one file per collection

If your platform requires multiple output files per theme, you can handle this in your build process.

## For More Information

- See [EXAMPLES.md](./EXAMPLES.md) for template examples in different formats
- See the [Adapter Development Guide](https://github.com/black-atom-industries/core/blob/main/ADAPTER_DEVELOPMENT.md) in the core repository for detailed documentation

## License

MIT © Black Atom Industries
