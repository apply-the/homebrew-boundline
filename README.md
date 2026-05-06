# homebrew-boundline

Official Homebrew tap repository for Boundline.

## Install

```bash
brew tap apply-the/boundline
brew install boundline
boundline doctor --install
```

The `boundline` formula builds the latest tagged Boundline release from the
source repository and stages the Canon companion pinned by that release so the
default `doctor --install` pairing story stays intact.

## Local Tap Development

```bash
brew tap apply-the/boundline /Users/rt/workspace/apply-the/homebrew-boundline
brew reinstall apply-the/boundline/boundline
```

## Maintainer Notes

This tap updates itself from the latest tagged Boundline release via
`.github/workflows/sync-latest-boundline-tag.yml`.

Operational notes:

- The tap-local workflow resolves the latest semver tag from `apply-the/boundline`
	and copies `distribution/homebrew/Formula/boundline.rb` from that exact tag.
- The workflow uses this repository's `GITHUB_TOKEN` with `contents: write` to
	commit directly to `main` when the formula changes.
- If branch protection is enabled here, allow GitHub Actions to push to `main`
	or replace the default token with a repository secret for a bot account.

## Release Checklist

1. In `apply-the/boundline`, push the release tag after the tagged source repo
	contains the correct `distribution/homebrew/Formula/boundline.rb`.
2. Wait for or manually run `.github/workflows/sync-latest-boundline-tag.yml`
	in this repository.
3. Verify the published tap with `brew reinstall apply-the/boundline/boundline`
	and `boundline doctor --install`.

## Contents

- `Formula/boundline.rb`: builds Boundline from the tagged source repo and
	stages the pinned Canon companion from the Canon source repo.
