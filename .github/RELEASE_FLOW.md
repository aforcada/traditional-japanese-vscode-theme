# Release Process Flow

```
┌─────────────────────────────────────────────────────────────────┐
│                    START: Manual Trigger                        │
│         (Go to Actions → Release → Run workflow)                │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             │ Input: version + changelog
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│  Step 1: Validate Version Format                                │
│  ✓ Check format is X.Y.Z (e.g., 1.4.0)                         │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│  Step 2: Update package.json                                    │
│  ✓ Set version to new version number                            │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│  Step 3: Update CHANGELOG.md                                    │
│  ✓ Add new entry at top with current date                       │
│  ✓ Include changelog text provided                              │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│  Step 4: Create Git Commit                                      │
│  ✓ Commit: "chore: release version X.Y.Z"                       │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│  Step 5: Create and Push Git Tag                                │
│  ✓ Tag: vX.Y.Z                                                  │
│  ✓ Push commit and tag to main                                  │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│  Step 6: Package Extension                                      │
│  ✓ Run: pnpm run package                                        │
│  ✓ Creates: .vsix file                                          │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│  Step 7: Publish to VS Code Marketplace                         │
│  ✓ Run: vsce publish                                            │
│  ✓ Uses: VSCE_TOKEN secret                                      │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│  Step 8: Create GitHub Release                                  │
│  ✓ Title: vX.Y.Z                                                │
│  ✓ Notes: changelog text                                        │
│  ✓ Attach: .vsix file                                           │
└────────────────────────────┬────────────────────────────────────┘
                             │
                             ▼
┌─────────────────────────────────────────────────────────────────┐
│                     SUCCESS! 🎉                                 │
│                                                                  │
│  ✅ Version updated in package.json                             │
│  ✅ CHANGELOG.md updated                                        │
│  ✅ Git tag created and pushed                                  │
│  ✅ Extension published to Marketplace                          │
│  ✅ GitHub release created                                      │
└─────────────────────────────────────────────────────────────────┘
```

## Time Estimate
⏱️ Total time: ~2-5 minutes (automated)

## Manual Steps Required
👤 Only 1 action: Trigger the workflow with version & changelog

## What You Get
📦 Complete release package ready for users
🚀 Available on VS Code Marketplace immediately
📝 Documentation updated automatically
🏷️ Version tagged in git
💾 Release artifacts saved to GitHub
