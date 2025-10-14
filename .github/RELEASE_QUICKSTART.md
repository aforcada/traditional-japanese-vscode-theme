# Release Automation - Quick Guide

## Quick Start

1. Go to **Actions** → **Release** workflow → **Run workflow**
2. Enter version (e.g., `1.4.0`) and changelog
3. Click **Run workflow**
4. Done! ✅

## What Gets Automated

- ✅ Updates `package.json` version
- ✅ Updates `CHANGELOG.md` with new entry
- ✅ Creates Git tag (`vX.Y.Z`)
- ✅ Publishes to VS Code Marketplace
- ✅ Creates GitHub Release with `.vsix` file

## Setup Required (One-time)

Create a secret named `VSCE_TOKEN`:
1. Get PAT from https://dev.azure.com/ (Marketplace: Acquire, Manage)
2. Add to GitHub: Settings → Secrets → Actions → New secret
3. Name: `VSCE_TOKEN`, Value: your PAT

See [RELEASE.md](RELEASE.md) for detailed documentation in Catalan.
