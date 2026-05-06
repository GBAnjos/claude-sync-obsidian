# Claude Sync

An Obsidian plugin that automatically imports Claude chat exports from a watched folder into your vault.

## Features

- **Auto-import**: Watches a folder for new markdown files and imports them to your vault
- **Folder preservation**: Maintains subdirectory structure from the watch folder
- **Configurable**: Set custom watch folder, vault destination, and check interval
- **Manual sync**: Trigger imports manually via command or ribbon icon
- **Clean imports**: Optionally delete source files after successful import

## Installation

### Manual Installation

1. Download the latest release (`main.js`, `manifest.json`, `styles.css`)
2. Create a folder called `claude-sync` in your vault's `.obsidian/plugins/` directory
3. Copy the downloaded files into the `claude-sync` folder
4. Enable the plugin in Obsidian Settings > Community Plugins

### From Source

```bash
git clone https://github.com/GBAnjos/claude-sync-obsidian
cd claude-sync-obsidian
# Copy files to your vault
cp main.js manifest.json styles.css /path/to/vault/.obsidian/plugins/claude-sync/
```

## Usage

### With Claude to Obsidian Chrome Extension

This plugin is designed to work with the [Claude to Obsidian](https://github.com/GBAnjos/claude-to-obsidian) Chrome extension:

1. Install this plugin in Obsidian
2. Install the Chrome extension
3. Set the watch folder in plugin settings (default: `~/Downloads/Claude Exports`)
4. Export chats from Claude using the extension's "Download" option
5. Files are automatically imported to your vault

### Standalone Usage

You can also use this plugin standalone:

1. Configure the watch folder to any directory
2. Drop `.md` files into the watch folder
3. They'll be automatically imported to your vault

## Settings

| Setting | Description | Default |
|---------|-------------|---------|
| Watch folder | Full path to folder to watch for exports | `~/Downloads/Claude Exports` |
| Vault folder | Folder inside vault where chats are saved | `Claude Chats` |
| Delete after import | Remove files from watch folder after importing | Enabled |
| Show notifications | Display notification when files are imported | Enabled |
| Check interval | How often to check for new files (seconds) | 5 |

## Commands

- **Claude Sync: Sync now** - Manually import all files from watch folder
- **Claude Sync: Open watch folder** - Open the watch folder in your file manager

## How It Works

1. The plugin polls the watch folder at the configured interval
2. When new `.md` files are found, they're read and created in the vault
3. Subdirectory structure is preserved (e.g., `watch/project/chat.md` → `vault/Claude Chats/project/chat.md`)
4. If "Delete after import" is enabled, source files are removed
5. Empty directories in the watch folder are cleaned up

## Troubleshooting

**Files not importing?**
- Check that the watch folder path is correct in settings
- Ensure the folder exists (use "Open watch folder" to create it)
- Verify files have `.md` extension

**Duplicate files?**
- The plugin skips files that already exist in the vault
- To re-import, delete the file from the vault first

## License

MIT

## Credits

Created for use with the [Claude to Obsidian](https://github.com/GBAnjos/claude-to-obsidian) project.
