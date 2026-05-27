---
{"dg-publish":true,"permalink":"/0x/htb/cjca/linux/package-management/","created":"2026-04-12T13:46:04.889+01:00","dg-note-properties":{}}
---

Here is a list of examples of such programs:

|**Command**|**Description**|
|---|---|
|`dpkg`|The `dpkg` is a tool to install, build, remove, and manage Debian packages. The primary and more user-friendly front-end for `dpkg` is aptitude.|
|`apt`|Apt provides a high-level command-line interface for the package management system.|
|`aptitude`|Aptitude is an alternative to apt and is a high-level interface to the package manager.|
|`snap`|Install, configure, refresh, and remove snap packages. Snaps enable the secure distribution of the latest apps and utilities for the cloud, servers, desktops, and the internet of things.|
|`gem`|Gem is the front-end to RubyGems, the standard package manager for Ruby.|
|`pip`|Pip is a Python package installer recommended for installing Python packages that are not available in the Debian archive. It can work with version control repositories (currently only Git, Mercurial, and Bazaar repositories), logs output extensively, and prevents partial installs by downloading all requirements before starting installation.|
|`git`|Git is a fast, scalable, distributed revision control system with an unusually rich command set that provides both high-level operations and full access to internals.|
 Most Linux distributions utilize the most stable or "main" repository. This can be checked by viewing the contents of the `/etc/apt/sources.list` file.

APT uses a database called the APT cache. This is used to provide information about packages installed on our system offline. We can search the APT cache, for example, to find all `Impacket` related packages.

###### List all installed packages:
`apt list --installed`

### Git and wget:
`git clone` is a useful command to installed packages:

```shell
git clone https://github.com/Hackplayers/evil-winrm.git
```

same as

```shell
wget clone https://github.com/Hackplayers/evil-winrm.git
```
