# Changesets

This folder was generated to manage versioning and changelog entries with [Changesets](https://github.com/changesets/changesets).

## Adding a release note

Run `pnpm changeset` and follow the prompts:

- choose the bump type (patch, minor, major)
- write a short summary of the change

The command creates a file inside `.changeset/` that is consumed when the automation prepares the next release.

## When a release is cut

Once pending changesets land on `main`, the GitHub workflow will:

1. run `changeset version` to update `package.json` and `CHANGELOG.md`
2. package the extension and publish it to the Marketplace
3. create git tags and a GitHub Release with the generated notes

No files in this folder should be edited manually unless you know what you are doing.
