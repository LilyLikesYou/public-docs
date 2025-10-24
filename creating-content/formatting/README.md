---
description: Learn the basic concepts and features to get the most out of our software
icon: i-cursor
---

# Basic Usage

This guide covers the fundamental features and concepts you need to understand to use our software effectively.

## Core Concepts

### Projects

A project is the top-level container for your work. Each project can contain:

- Configuration files
- Data files
- Resource definitions
- Output artifacts

**Creating a project:**

```bash
your-software create-project my-project
cd my-project
```

### Workspaces

Workspaces organize related projects and allow you to work on multiple projects simultaneously. Think of them as folders that group related work.

**Switching workspaces:**

```bash
your-software workspace list
your-software workspace switch my-workspace
```

### Resources

Resources are the building blocks of your projects. They represent entities like:

- Data sources
- Processing pipelines
- Output destinations
- Configuration templates

**Defining a resource:**

```yaml
# resource.yml
name: my-resource
type: processor
config:
  input: data.csv
  output: results.json
```

## Basic Operations

### Creating and Managing Files

**Create a new file:**

```bash
your-software create file --name data.csv
```

**List files:**

```bash
your-software list files
```

**Delete a file:**

```bash
your-software delete file data.csv
```

### Running Commands

The most common command you'll use is `run`, which executes your project:

```bash
your-software run
```

**With options:**

```bash
your-software run --env production --verbose
```

**Dry run (preview without executing):**

```bash
your-software run --dry-run
```

### Viewing Status

Check the status of your project at any time:

```bash
your-software status
```

This shows:
- Current workspace
- Active resources
- Recent operations
- System health

## Configuration

### Configuration Files

Your project's behavior is controlled by configuration files. The main configuration file is `config.yml` or `config.json`.

**Example config.yml:**

```yaml
version: 1.0
project:
  name: my-project
  description: My awesome project
  
settings:
  timeout: 30
  retries: 3
  log_level: info

resources:
  - name: data-source
    type: input
    path: ./data/input.csv
    
  - name: processor
    type: transform
    script: ./scripts/process.py
```

### Environment Variables

Override configuration with environment variables:

```bash
export YOUR_SOFTWARE_API_KEY=your-key-here
export YOUR_SOFTWARE_ENV=production
```

Or use a `.env` file:

```bash
YOUR_SOFTWARE_API_KEY=your-key-here
YOUR_SOFTWARE_ENV=production
YOUR_SOFTWARE_LOG_LEVEL=debug
```

## Working with Data

### Importing Data

Import data from various sources:

```bash
# From a file
your-software import --source data.csv

# From a URL
your-software import --source https://example.com/data.json

# From a database
your-software import --source "postgresql://localhost/mydb"
```

### Exporting Data

Export processed data to different formats:

```bash
# As JSON
your-software export --format json --output results.json

# As CSV
your-software export --format csv --output results.csv

# To a database
your-software export --destination "postgresql://localhost/mydb"
```

### Data Transformations

Apply transformations to your data:

```bash
your-software transform --input data.csv --operations filter,sort,aggregate
```

## Best Practices

### Project Organization

Keep your projects organized:

```
my-project/
├── config.yml          # Main configuration
├── .env               # Environment variables
├── data/              # Data files
│   ├── input/
│   └── output/
├── scripts/           # Custom scripts
├── resources/         # Resource definitions
└── docs/             # Project documentation
```

### Version Control

Always use version control for your projects:

```bash
git init
git add .
git commit -m "Initial commit"
```

Add a `.gitignore` file:

```
.env
data/output/
*.log
.cache/
```

### Error Handling

Enable detailed logging when troubleshooting:

```bash
your-software run --log-level debug
```

Check logs:

```bash
your-software logs --tail 100
```

## Next Steps

Now that you understand the basics, explore more advanced features:

- [Advanced Features](../blocks/) - Learn about powerful capabilities
- [API Reference](../../api-references/openapi/) - Detailed API documentation
- [Configuration Guide](../../getting-started/git-sync/) - Advanced configuration options
- [Examples](https://github.com/your-org/examples) - Sample projects

## Getting Help

- Review [common issues](../../help/connectivity-issues.md)
- Check the [FAQ](../../help/faqs.md)
- Ask in [community forums](https://github.com/your-org/discussions)
- [Contact support](../../help/support.md)

{% hint style="success" %}
**Pro Tip**: Use `your-software --help` to see all available commands and options at any time.
{% endhint %}

{% hint style="info" %}
**Note**: Replace `your-software` with your actual software name throughout your documentation.
{% endhint %}
