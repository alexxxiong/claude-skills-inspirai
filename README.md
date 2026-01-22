# InspirAI Claude Skills

A Claude Code plugin for managing API documentation across InspirAI projects.

## Features

- **api-init** - Initialize API documentation config for backend projects
- **api-update** - Parse routes and generate API documentation
- **api-lookup** - Query API documentation across projects

## Installation

### Via Claude Code Plugin Marketplace

```bash
# Add marketplace (if not already added)
claude plugins add-marketplace https://github.com/alexxxiong/claude-skills-inspirai

# Install plugin
claude plugins install inspirai
```

### Manual Installation

```bash
git clone https://github.com/alexxxiong/claude-skills-inspirai.git ~/.claude/plugins/inspirai
```

## Setup

Before using these skills, clone the API specs repository:

```bash
git clone git@github.com:alexxxiong/inspirai-api-specs.git ~/.inspirai/apilookup
```

## Usage

### Initialize a Project

```bash
/api-init
```

Creates `.api-spec.yaml` in your project root with:
- Project name and description
- Base URL
- Routes file location
- Project type (go/node/python)

### Update API Documentation

```bash
/api-update              # Update all APIs
/api-update auth         # Update only auth module
```

Parses your routes and handlers, generates YAML documentation, and pushes to the spec repository.

### Lookup API Documentation

```bash
/api-lookup                              # List all projects
/api-lookup inspirai-user                # Show all APIs for a project
/api-lookup inspirai-user auth           # Show auth module APIs
/api-lookup inspirai-user auth/sms-login # Show specific API details
```

## Directory Structure

```
~/.inspirai/apilookup/
├── meta.yaml                    # Global project index
├── inspirai-user/
│   ├── meta.yaml               # Project API index
│   ├── auth/
│   │   ├── sms-send.yaml
│   │   └── sms-login.yaml
│   ├── user/
│   ├── email/
│   └── ...
└── another-project/
    └── ...
```

## License

MIT
