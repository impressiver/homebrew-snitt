# Homebrew tap for Snitt

[Snitt](https://github.com/impressiver/snitt) is a native macOS screen
recorder that a coding agent can drive.

```sh
brew tap impressiver/snitt
brew install --cask snitt
```

## What this repo is

One file: `Casks/snitt.rb`. Homebrew resolves `brew tap <user>/<name>` to a
repository literally named `homebrew-<name>`, which is the only reason this
exists as a separate repo rather than as a directory in the main one.

**The cask is generated, not authored here.** `Casks/snitt.rb` in the
[main repository](https://github.com/impressiver/snitt/blob/main/Casks/snitt.rb)
is the source of truth: `Scripts/release.sh` rewrites its version and hash on
every release, in the same commit as the version bump, so the two cannot
diverge. A copy lands here per release.

So an edit made **here** is one the next release overwrites. Fix the cask in
the main repository instead.

## Updating, not upgrading

The cask declares `auto_updates true`, because Snitt updates itself through
Sparkle. Homebrew is how you install it, not how it stays current, and
declaring that stops `brew upgrade` reinstalling a version it knows over a
newer one the app has already fetched for itself.
