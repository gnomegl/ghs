# gh-search

[![basher install](https://www.basher.it/assets/logo/basher_install.svg)](https://www.basher.it/package/)

github repository search with contributor enumeration

## install

```bash
basher install gnomegl/gh-search
```

## usage

```bash
gh-search [term]
```

search repos by keyword, email, author, org, or user. enumerate contributors with `-c`.

## options

- `-l, --limit` - results limit (default: 10)
- `-e, --email` - search by contributor email
- `-a, --author` - search by commit author
- `-o, --org` - search in organization
- `-u, --user` - search user's repos
- `-c, --contributors` - enumerate all contributors
- `-j, --json` - output raw json

## requirements

- curl
- jq
- git