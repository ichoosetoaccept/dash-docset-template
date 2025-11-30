# Dash Docset Template

A [Copier](https://github.com/copier-org/copier) template for creating Dash docset generators.

## Features

- Complete project scaffold for building Dash docsets
- Web scraper with support for sitemap.xml or llms.txt URL discovery
- SQLite search index builder with customizable parsers
- TOC anchor injection for in-page navigation
- Docset validation script
- Pre-commit hooks with prek (ty type checking, standard hooks)
- uv for dependency management

## Usage

### Install Copier

```bash
# With uv
uv tool install copier

# Or with pipx
pipx install copier
```

### Create a new docset project

```bash
copier copy gh:YOUR_USERNAME/dash-docset-template my-new-docset

# Or from a local clone
copier copy /path/to/dash-docset-template my-new-docset
```

### Answer the prompts

- **project_name**: Name of your project (e.g., `raycast-docset`)
- **docset_name**: Display name for the docset (e.g., `Raycast`)
- **docs_url**: Base URL of documentation (e.g., `https://developers.raycast.com`)

### Set up the generated project

```bash
cd my-new-docset
uv sync
prek install
```

### Customize

1. **Scraper** (`*_docset/scraper.py`): Adjust URL discovery and filtering
2. **Parsers** (`*_docset/parsers.py`): Add custom parsers for different page types
3. **Builder** (`*_docset/builder.py`): Customize icon URL and path handling

### Build the docset

```bash
uv run python main.py --scrape
```

## Template Structure

```
dash-docset-template/
├── copier.yaml                       # Template configuration
├── template/
│   ├── {{docset_identifier}}_docset/ # Package (name templated)
│   │   ├── __init__.py.jinja
│   │   ├── scraper.py.jinja          # Auto-detects sitemap/llms.txt
│   │   ├── builder.py.jinja
│   │   └── parsers.py.jinja
│   ├── main.py.jinja
│   ├── verify.py.jinja
│   ├── pyproject.toml.jinja
│   ├── README.md.jinja
│   ├── .gitignore
│   └── .pre-commit-config.yaml
└── README.md
```

## License

MIT
