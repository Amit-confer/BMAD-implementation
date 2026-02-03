# CLI Command Reference

## Overview
The ToolJet CLI is built with **Oclif** and provides utilities for managing ToolJet installations and plugins.

**Binary Name**: `tooljet`

## Commands

### Global
#### `info`
Returns information about the runtime environment (OS, Node version, ToolJet version).
- **Usage**: `tooljet info`

### Plugins (`plugin`)
Manage ToolJet marketplace plugins.

#### `plugin:create`
Scaffolds a new plugin.
- **Usage**: `tooljet plugin:create`
- **Arguments**: Interactive prompts for plugin name, type, and description.

#### `plugin:install`
Installs a plugin into the system.
- **Usage**: `tooljet plugin:install [plugin]`

#### `plugin:delete`
Removes a plugin.
- **Usage**: `tooljet plugin:delete [plugin]`

## Development
To run the CLI locally:
1. `cd cli`
2. `npm install`
3. `npm run build`
4. `./bin/run [command]`
