# Black Atom Adapter Template

This repository provides a template for creating new Black Atom theme adapters. It includes the basic structure and configuration needed to adapt Black Atom themes to a new platform.

## Getting Started

1. Clone this repository
2. Rename it to match your target platform (e.g., `vscode`, `alacritty`)
3. Update the basic files below to match your platform needs

## Repository Structure

```
.
├── LICENSE                   # MIT license
├── README.md                 # This documentation
├── EXAMPLES.md               # Example templates in different formats
├── black-atom-adapter.json   # Adapter configuration file
└── themes/                   # Template directory
    ├── stations/             # Stations collection templates
    │   └── collection.template.json
    ├── jpn/                  # JPN collection templates
    │   └── collection.template.json
    ├── crbn/                 # CRBN collection templates
    │   └── collection.template.json
    └── terra/                # Terra collection templates
        └── collection.template.json
```

## Setup Steps

1. **Update README.md** - Customize this file with platform-specific information
2. **Edit black-atom-adapter.json** - Configure collection-based templates
3. **Create collection templates** - Create or modify `.template.{ext}` files for each collection
4. **Test your adapter** - Run `black-atom-core adapt` to generate theme files

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
