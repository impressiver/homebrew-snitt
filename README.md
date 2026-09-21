# Homebrew tap for Snitt

[Snitt](https://github.com/impressiver/snitt) is a native macOS screen
recorder that a coding agent can drive.

```sh
brew tap impressiver/snitt
brew trust impressiver/snitt
brew install --cask snitt
```

The middle line is not optional and is easy to leave out of an install
snippet. Homebrew 7 refuses to load a cask from a third-party tap until the
tap is trusted, with:

```
Error: Refusing to load cask impressiver/snitt/snitt from untrusted tap
impressiver/snitt.
```

That is Homebrew asking whether you mean to run a formula from someone who
is not Homebrew, which is a fair question and the reason a tap is one repo
with no review queue.

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

## Licence

[Mozilla Public License 2.0](LICENSE), the same as
[Snitt itself](https://github.com/impressiver/snitt).

Not a choice this repository got to make. `Casks/snitt.rb` is copied from a
repository under MPL-2.0, and the MPL is file-level copyleft: a copy of a
covered file stays covered wherever it goes. Naming the same licence here is
the honest description of what is already true, rather than a second set of
terms for one file to be under.

The cask carries its own notice for the same reason, so the file says what it
is without anyone having to find this README first.
