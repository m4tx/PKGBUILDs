# PKGBUILDs

[![Test status](https://github.com/m4tx/pkgbuilds/actions/workflows/test.yml/badge.svg)](https://github.com/m4tx/pkgbuilds/actions)

## Managing packages

Each package is managed as a git [subtree](https://git-scm.com/book/en/v2/Git-Tools-Advanced-Merging#_subtree_merge).
Changes are automatically pushed to the AUR on commits to master.

[nvchecker](https://github.com/lilydjwg/nvchecker) is used to check upstream repositories for new versions nightly.
Pull requests to update versions are generated at midnight (PST).

### Adding a new package

```shell
git subtree add --prefix=$PACKAGE ssh://aur@aur.archlinux.org/$PACKAGE.git master
```

Add the package to `nvchecker.toml` and `.pre-commit-config.yaml` for CI/CD.
Verify the package will build in CI,

```shell
./build $PACKAGE
```

## Running tests

As recommended by the [Arch Wiki](https://wiki.archlinux.org/title/PKGBUILD), `namcap` and
`shellcheck` are configured to check the PKGBUILDs.

Each can be ran with the following commands,

```shell
./shellcheck
```

```shell
./namcap
```

## Attribution

This repository is based on [jmelahman/PKGBUILDs](https://github.com/jmelahman/PKGBUILDs/tree/master), licensed under the MIT license:

```
MIT License

Copyright (c) 2024 Jamison Lahman

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
