# mpls.bike

This is the source code for mpls.bike and some tools for managing it.

## Website

Install [hugo](https://gohugo.io/).

```bash
brew install hugo
cd website
hugo serve
```

Updating the website event data requires the latest data from google calendar merged with the latest SQLIte DB. 

```bash
mise run pull
calsync fetch-events
hugo serve
```

See `.github/workflows/sync.yml` for details.

## Management Tools

1. Install [`uv`](https://docs.astral.sh/uv/)
1. `uv sync`
1. `cp .env.example .env` and then edit `.env` with API keys.

The calendar management tool relies on a SQLite database that is kept in a google cloud bucket.

Running calendar sync:

```bash
# Check that things are installed correctly
calsync --help
# Pull the latest DB
mise run pull
# Run
calsync process
# Push the DB
mise run push
```

Triggering a github action workflow:

```bash
mise run trigger

# optionally watch it from the command line
gh run list
gh run watch
```

Code validation

```bash
mise run validate
```
