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
    └── example.template.json # Example template file
```

## Setup Steps

1. **Update README.md** - Customize this file with platform-specific information
2. **Edit black-atom-adapter.json** - Map themes to your template files
3. **Create template files** - Add `.template.{ext}` files for each theme
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

The `black-atom-adapter.json` file maps theme keys to template files:

```json
{
  "black-atom-stations-engineering": {
    "templates": ["./themes/example.template.json"]
  },
  "black-atom-jpn-koyo-yoru": {
    "templates": ["./themes/jpn.template.css"]
  }
}
```

You can define multiple templates per theme if your platform requires multiple output files.

## For More Information

- See [EXAMPLES.md](./EXAMPLES.md) for template examples in different formats
- See the [Adapter Development Guide](https://github.com/black-atom-industries/core/blob/main/ADAPTER_DEVELOPMENT.md) in the core repository for detailed documentation

## License

MIT © Black Atom Industries
