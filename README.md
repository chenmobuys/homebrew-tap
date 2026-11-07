# chenmobuys Homebrew tap

[![Cask checks](https://github.com/chenmobuys/homebrew-tap/actions/workflows/ci.yml/badge.svg)](https://github.com/chenmobuys/homebrew-tap/actions/workflows/ci.yml)

Homebrew definitions for apps maintained by chenmobuys. Application source code and release installers remain in their own repositories.

## Neylu

A compact, native macOS menu bar system monitor. Requires macOS 13 or later; Apple Silicon and Intel installers are selected automatically.

```sh
brew install --cask chenmobuys/tap/neylu
```

The current release is an Alpha preview, ad hoc signed and not notarized by Apple. See [Neylu’s first-launch instructions](https://github.com/chenmobuys/Neylu#readme) if macOS prevents it from opening. No Apple Developer membership is required. This cask does not remove quarantine attributes or disable Gatekeeper.

安装后会直接显示首次打开说明；若 macOS 拦截，确认信任此版本后执行以下命令，再重新打开 Neylu。
Homebrew prints first-launch instructions after installation. If macOS blocks Neylu and you trust this release, run the following, then reopen it:

```sh
xattr -dr com.apple.quarantine "/Applications/Neylu.app"
```

You can also install and explicitly allow the first launch with one command:

```sh
brew install --cask chenmobuys/tap/neylu &&
xattr -dr com.apple.quarantine "/Applications/Neylu.app"
```

These examples use the default Applications directory. If you use `--appdir`, follow the actual path printed by Homebrew. Alternatively, choose **Open Anyway** in **System Settings → Privacy & Security**.

```sh
brew update
brew upgrade --cask --greedy neylu
```

`--greedy` includes apps with built-in updaters. `brew uninstall --cask neylu` preserves local history and preferences. Adding `--zap` deletes them.

## Automated maintenance

After a successful [Neylu release](https://github.com/chenmobuys/Neylu/releases), its Homebrew workflow downloads both published installers, verifies their size and GitHub SHA-256 digests, and commits the generated cask directly to this repository using a dedicated deploy key. No manual pull-request merge is required.

Updates are serialized. Older releases cannot downgrade the cask, and a same-version checksum change is rejected. Rerunning the workflow for the installed cask version is a no-op. Every cask push runs this repository’s syntax and Homebrew style checks.

A failed synchronization can be retried from [Neylu’s Homebrew workflow](https://github.com/chenmobuys/Neylu/actions/workflows/homebrew.yml) without rebuilding or replacing release assets.

This is a third-party tap, not inclusion in the official Homebrew Cask repository.
