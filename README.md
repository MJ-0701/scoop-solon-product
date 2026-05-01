# Solon Product Scoop Bucket

Scoop bucket for the Solon Product SFS runtime.

## Install

```powershell
scoop bucket add solon https://github.com/MJ-0701/scoop-solon-product
scoop install sfs
```

## First Project Setup

```powershell
cd C:\workspace\my-project
git init
sfs init --layout thin --yes
sfs status
sfs agent install all
```

Solon SFS on Windows requires Git for Windows/Git Bash. If `bash.exe` is not on
`PATH`, set `SFS_BASH` to the full `bash.exe` path before running `sfs`.

## Release Maintenance

When releasing a new `solon-product` tag, update this bucket alongside the
Homebrew tap:

1. Confirm the new product tag exists, for example `v0.5.43-product`.
2. Download the exact GitHub tag zip.
3. Compute its SHA256.
4. Update `bucket/sfs.json` fields: `version`, `url`, `hash`, and `extract_dir`.
5. Commit and push this bucket repo.
6. Smoke test on Windows:

```powershell
scoop update
scoop update sfs
sfs version
```
