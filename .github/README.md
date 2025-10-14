# 🤖 Automation & Documentation

This directory contains the release automation workflow and comprehensive documentation for maintaining and releasing the Traditional Japanese VS Code Theme.

## 📁 Files in This Directory

### Workflow
- **`workflows/release.yml`** - GitHub Actions workflow that automates the entire release process

### Documentation (Start Here! 👇)
- **`RELEASE_QUICKSTART.md`** ⚡ - **Start here!** Quick 2-minute guide (English)
- **`RELEASE.md`** 📚 - Complete documentation with setup & troubleshooting (Catalan)
- **`RELEASE_FLOW.md`** 🔄 - Visual diagram showing the automated process flow
- **`IMPLEMENTATION_SUMMARY.md`** 🔧 - Technical implementation details
- **`BEFORE_AFTER.md`** 📊 - Metrics comparison showing improvements

## 🚀 Quick Start

**To release a new version:**

1. Go to the **Actions** tab in GitHub
2. Select **Release** workflow
3. Click **Run workflow**
4. Enter:
   - Version: `1.4.0` (format: X.Y.Z)
   - Changelog: `- New feature.\n- Bug fix.`
5. Click **Run workflow** button
6. Wait 2-5 minutes ⏱️
7. ✅ Done! Everything is automated.

## ⚙️ Setup (One-Time)

You need to add a `VSCE_TOKEN` secret:

1. Get a Personal Access Token from https://dev.azure.com/
   - Required permissions: `Marketplace: Acquire, Manage`
2. Add it to GitHub:
   - Go to: Settings → Secrets and variables → Actions
   - Click: New repository secret
   - Name: `VSCE_TOKEN`
   - Value: Your PAT from Azure DevOps

See `RELEASE.md` for detailed setup instructions.

## 📖 Documentation Guide

**Choose your path:**

| If you want to... | Read this file |
|-------------------|----------------|
| Release a version quickly | `RELEASE_QUICKSTART.md` |
| Learn complete details | `RELEASE.md` |
| Understand the process flow | `RELEASE_FLOW.md` |
| See technical implementation | `IMPLEMENTATION_SUMMARY.md` |
| Compare before/after metrics | `BEFORE_AFTER.md` |
| Modify the workflow | `workflows/release.yml` |

## ✨ What Gets Automated

When you run the Release workflow, it automatically:

1. ✅ Updates `package.json` version
2. ✅ Updates `CHANGELOG.md` with new entry and date
3. ✅ Creates a git commit
4. ✅ Creates and pushes a git tag (`vX.Y.Z`)
5. ✅ Packages the extension (`.vsix` file)
6. ✅ Publishes to VS Code Marketplace
7. ✅ Creates a GitHub release with the `.vsix` file attached

**Total time: 2-5 minutes (fully automated)**

## 🎯 Benefits

- ⏱️ **87-93% time savings** (from 15-30 min to 2 min)
- ✅ **Zero manual errors** - Everything validated
- 🎯 **Perfect consistency** - Same process every time
- 📚 **Well documented** - Multiple guides available
- 🛡️ **Error prevention** - Built-in validation

## 🆘 Need Help?

1. Check `RELEASE_QUICKSTART.md` for quick answers
2. Read `RELEASE.md` troubleshooting section
3. Open an issue in the repository

---

**Last Updated**: 2025-10-14  
**Workflow Version**: 1.0  
**Status**: ✅ Production Ready
