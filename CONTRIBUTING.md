# Pluggable Transports Software Repository

This guide explains how to add your pluggable transports software to
<https://software.pluggabletransports.info/>


## 🚀 Quick info

- A package entry in the "Pluggable Transports Repository" index is managed by a
  single [YAML](https://en.wikipedia.org/wiki/YAML) file.
  [See below `packages/pkg-example.yaml`](#example-package-entry),
  for an example package called "pkg-example".

- Adding or updating your package is done by a
  [**pull request**](https://docs.github.com/en/github/getting-started-with-github/github-glossary#pull-request).
  The pull request is reviewed
  [automatically via GitHub Actions](https://github.com/Pluggable-Transports/Pluggable-Transports-software/actions)
  and has to be approved and merged manually.

  > If the automatic GitHub Actions review fails,
  > please [create an issue](https://github.com/Pluggable-Transports/Pluggable-Transports-software/issues)
  > to resolve the problem.


## ✅ Add your package

- Copy the [example package entry](#example-package-entry) below
  and adapt it to your package.

- Create file `packages/<my package>.yaml` with the name of your package in the
  [packages](https://github.com/Pluggable-Transports/Pluggable-Transports-software/tree/main/packages)
  subdirectory.

  To do this, either use the "easy" way by following the
  [GitHub guide how to create a new file](https://docs.github.com/en/github/managing-files-in-a-repository/creating-new-files)
  ...

  ... or for experts:
  - fork <https://github.com/Pluggable-Transports/Pluggable-Transports-software>
  - clone your fork `https://github.com/<my username>/packages`
  - add `packages/<my package>.yaml`
  - commit and push the changes to your fork
  - finally [create a pull request](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request).


## 🔄 Update your package

- For example after a new release of your package you can update the index
  entry by editing the file `packages/<my package>.yaml` with the name of your
  package in the
  [packages](https://github.com/Pluggable-Transports/Pluggable-Transports-software/tree/main/packages)
  subdirectory.

  To do this, either use the "easy" way by following the
  [GitHub guide how to edit files](https://docs.github.com/en/github/managing-files-in-a-repository/editing-files-in-your-repository)
  and the
  [GitHub guide how to edit files in other repositories](https://docs.github.com/en/github/managing-files-in-a-repository/editing-files-in-another-users-repository)
  ...

  ... or expert users can work in a fork as described above.


## 🔰 Example package entry

An example package entry
[`packages/pkg-example.yaml`](https://github.com/Pluggable-Transports/Pluggable-Transports-software/blob/main/packages/pkg-example.yaml)
(see [output](https://software.pluggabletransports.info/packages/pkg-example)):

```yaml
layout: "package"
permalink: "pkg-example"
description: >-
  Example package to demonstrate the creation process of a PT package. Keep this
  description brief. Describe the major features in the first two lines (160
  characters).

  Multiple lines are allowed. Each line may have maximal 80 characters.
  Exceptions are URLs. Paragraphs, blank lines, and line breaks are ignored and
  replaced by spaces.
icon: "https://raw.githubusercontent.com/gnu-octave/pkg-example/main/doc/icon.png"
links:
- icon: "far fa-copyright"
  label: "GPL-3.0-or-later"
  url: "https://github.com/gnu-octave/pkg-example/blob/main/COPYING"
- icon: "fas fa-rss"
  label: "news"
  url: "https://github.com/gnu-octave/pkg-example/releases/"
- icon: "fas fa-code-branch"
  label: "repository"
  url: "https://github.com/gnu-octave/pkg-example/"
- icon: "fas fa-book"
  label: "package documentation"
  url: "https://github.com/gnu-octave/pkg-example/blob/main/README.md"
- icon: "fas fa-bug"
  label: "report a problem"
  url: "https://github.com/gnu-octave/pkg-example/issues"
maintainers:
- name: "Kai T. Ohlhus"
  contact: "k.ohlhus@gmail.com"
- name: "Another Contactless Developer"
  contact:
versions:
- id: "1.1.0"
  date: "2021-04-06"
  url: "https://github.com/gnu-octave/pkg-example/archive/1.1.0.tar.gz"
- id: "1.0.0"
  date: "2020-09-02"
  url: "https://github.com/gnu-octave/pkg-example/archive/1.0.0.tar.gz"
languages:
- name: "C"
- name: "C++"
- name: "Fortran"
---
```


## 📚 Details

### ✏️ General specifications

- For technical reasons, the first and last line `---` of the file are
  fixed and may not be altered.

- Indent by 2 spaces (no tabs) and leave one space after colon `:`.

- All strings must be enclosed with double quotes `"`.
  `description` is an exception using a
  [block style string](https://yaml.org/spec/1.2/spec.html#Block)
  marked by `>-`.  The `description` string is `>` folded (no literal line
  breaks) and `-` chopped by the final newline.


### 📑 Individual field explanations

- `layout`: fixed string `"package"` for technical reasons.

- `permalink`: string with the name of the package.
  **Must** match the file name.

- `description`: see example above.

- `icon`: URL string to a publicly accessible image.  It will be displayed with
  `50px` width in the [package index](https://software.pluggabletransports.info/packages/)
  and with `150px` with in the
  [individual package page](https://software.pluggabletransports.info/packages/packages/pkg-example).

- `links`: list containing three fields.

  - `icon`: any [free FontAwesome](https://fontawesome.com/icons?d=gallery&p=2&m=free)
    class string is permitted.  The icon is part of the hyperlink.

  - `label`: string of the hyperlink.

  - `url`: string of the hyperlink.

  You are free to choose any links in any order describing your package best.
  However, it has proved useful to give some basic information,
  as seen in the example above:

  - Link to your **license** or copyright information.
    For the label use an [SPDX string](https://spdx.org/licenses/),
    e.g. "GPL-3.0-or-later".

  - Link to release **news**.

  - Link to your development **repository**.

  - Link to your **package documentation** or homepage.

  - Link to **report a problem**.

- `maintainers`: list containing two fields.

  - `name`: maintainer name string.

  - `contact`: email address, homepage or other contact options.

- `versions`: list containing five fields.

  > **Note:** The first version in this list is regarded as recommended for
  > installation.  Avoid listing an unstable development version at the first
  > position.  It is recommended, not necessary, to sort your releases from
  > the newest (top) to the oldest (bottom).

  - `id`: unique identifier string for this version, e.g. `"1.0.1"`, `"dev"`,
    ...

  - `date`: date string in the format `"YYYY-MM-DD"` or blank if a date does
    not apply for the release type.

  - `url`: URL string of the release archive (tarball or zip file).

- `languages`: list containing one field.

  - `name`: language name string.
