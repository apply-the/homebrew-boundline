# homebrew-boundline

Official Homebrew tap repository for Boundline.

## Install

```bash
brew tap apply-the/boundline
brew install boundline
boundline doctor --install
```

The `boundline` formula builds Boundline `0.41.0` from the tagged source
repository and installs the pinned Canon `0.40.0` companion alongside it so the
default `doctor --install` pairing story stays intact.

## Local Tap Development

```bash
brew tap apply-the/boundline /Users/rt/workspace/apply-the/homebrew-boundline
brew reinstall apply-the/boundline/boundline
```

## Maintainer Notes

This tap is updated from the main Boundline repository by
`/Users/rt/workspace/synod/.github/workflows/sync-homebrew-tap.yml`.

Required setup in the source repository:

- Add the secret `HOMEBREW_TAP_GITHUB_TOKEN` in `apply-the/boundline`.
- The token must be able to read metadata and write contents plus pull requests
	in `apply-the/homebrew-boundline`.
- A fine-grained PAT scoped to `apply-the/homebrew-boundline` with
	`Contents: Read and write`, `Pull requests: Read and write`, and
	`Metadata: Read-only` is sufficient.

Operational notes:

- The sync workflow regenerates `distribution/homebrew/Formula/boundline.rb` in
	the source repo and opens a PR against this tap.
- No GitHub Actions secret is required in this tap repository unless you add
	tap-local workflows later.
- If branch protection is enabled here, ensure the token owner can push a
	branch and open pull requests.

## Contents

- `Formula/boundline.rb`: builds Boundline from the tagged source repo and
	stages the pinned Canon companion from the Canon source repo.
