# gh-search - GitHub Repository Search

[![Basher](https://img.shields.io/badge/basher-install-brightgreen)](https://github.com/basherpm/basher)

Advanced search tool for GitHub repositories with powerful contributor enumeration and analysis capabilities.

## Features

- **Advanced Search**: Search repositories by keywords, author, organization, and more
- **Contributor Enumeration**: Discover all contributors across repositories
- **Email Discovery**: Find commit author email addresses and patterns
- **Deep Analysis**: Analyze repository contents, commit patterns, and technologies
- **Flexible Filtering**: Filter by stars, forks, language, and other criteria
- **Multiple Output Formats**: JSON or formatted text output
- **Rate Limit Awareness**: Tracks and displays API rate limit status

## Installation

### Using Basher

```bash
basher install gnomegl/gh-search
```

### Manual Installation

```bash
git clone https://github.com/gnomegl/gh-search.git
cd gh-search
chmod +x bin/gh-search
# Add to PATH or copy to /usr/local/bin
```

## Usage

### Basic Search

```bash
# Search for repositories
gh-search "machine learning"

# Search in specific organization
gh-search "api" --org microsoft

# Search by user
gh-search "dotfiles" --user octocat
```

### Advanced Options

- `--limit, -l` - Number of results to display (default: 10)
- `--email, -e` - Search by contributor email (supports wildcards)
- `--author, -a` - Search by commit author name
- `--org, -o` - Search in specific organization
- `--user, -u` - Search in repositories owned by user
- `--sort, -s` - Sort by (stars, forks, updated)
- `--json, -j` - Output raw JSON
- `--deep, -d` - Perform deeper analysis on found repos
- `--fork, -f` - Include forked repositories
- `--contributors, -c` - Enumerate all contributors

### Contributor Enumeration

```bash
# Enumerate contributors in an organization
gh-search --contributors --org spearbit

# Enumerate contributors for a user
gh-search --contributors --user vitalik

# Include forked repositories in enumeration
gh-search --contributors --org ethereum --fork
```

### Examples

```bash
# Find repositories with specific email pattern
gh-search "security" --email "*@company.com"

# Deep analysis of search results
gh-search "blockchain" --deep --limit 5

# Search for recently updated repositories
gh-search "python" --sort updated --limit 20

# Get contributor data for organization
gh-search --contributors --org microsoft
```

## Contributor Enumeration Features

When using `--contributors`, the tool will:

- **Scan All Repositories**: Process every repository in the organization/user account
- **Extract Commit Data**: Gather direct commits (excluding merges)
- **Email Discovery**: Find email addresses from commit author data
- **Pattern Analysis**: Identify commit timing patterns and activity
- **Export Data**: Save results to timestamped JSON files
- **Domain Analysis**: Group emails by domain for analysis

### Output Files

- `direct-commit-authors-{type}-{name}-{timestamp}.json` - Complete contributor data
- Includes commit counts, email addresses, repository lists, and timestamps

## Authentication

The tool supports GitHub authentication via:

1. `~/.config/github/token` file
2. `GITHUB_TOKEN` environment variable
3. Existing `gh` CLI authentication

## Requirements

- `curl` - For API requests
- `jq` - For JSON processing
- `git` - For repository operations
- `trufflehog` - For secret scanning (optional)

## Rate Limits

- **Unauthenticated**: 60 requests per hour
- **Authenticated**: 5,000 requests per hour
- The tool displays remaining rate limit after each operation

## Use Cases

- **Security Research**: Find repositories with specific patterns
- **OSINT**: Gather intelligence on organizations and developers
- **Recruitment**: Identify active contributors in specific technologies
- **Compliance**: Audit code repositories for email patterns
- **Research**: Analyze development patterns and collaboration

## License

MIT License
