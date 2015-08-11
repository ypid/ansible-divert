## divert

[![Travis CI](http://img.shields.io/travis/ypid/ansible-divert.svg?style=flat)](http://travis-ci.org/ypid/ansible-divert)
[![Ansible Galaxy](http://img.shields.io/badge/galaxy-ypid.divert-660198.svg?style=flat)](https://galaxy.ansible.com/list#/roles/4668)
[![Platforms](http://img.shields.io/badge/platforms-debian%20/%20ubuntu-lightgrey.svg?style=flat)](#)
[![GitHub Tags](https://img.shields.io/github/tag/ypid/ansible-divert.svg)](https://github.com/ypid/ansible-divert)
[![GitHub Stars](https://img.shields.io/github/stars/ypid/ansible-divert.svg)](https://github.com/ypid/ansible-divert)


Simple role for package management aware renaming of files.

Allows to move files which were installed by a package and to inform the package manager about the change so that it can do the right thing when the moved file is later installed again by a package upgrade. The right thing in this context is to map all new versions to the diverted location and to avoid touching the original file location.

This role is intended to work with all package managers which can be informed about such changes.

### Currently supported packages managers

* [dpkg](https://en.wikipedia.org/wiki/Dpkg)

### Installation

This role requires at least Ansible `v1.8.4`. To install it, run:

```Shell
ansible-galaxy install ypid.divert
```

To install via git, run either:

```Shell
git clone https://github.com/ypid/ansible-divert.git ypid.divert
git submodule add https://github.com/ypid/ansible-divert.git ypid.divert
```




### Role variables

List of default variables available in the inventory:

```YAML
---

# original (string, required): File path of the original file.
#
# diverted (string, optional, default: original + diverted_files_default_suffix):
# File path where all new file versions created by package updates are
# redirected to.
#
# state (string, optional, default: 'present'):
# If 'present', the diversion should be enabled. If 'absent' the diversion will
# be removed.
#
# force (boolean, optional, default: false):
# If true and state is 'absent' the diversion will be removed even if that
# means that your modified file has to be deleted first to restore the original
# version of the package maintainer.
#
# copy (boolean, optional, default: false):
# Copy the diverted file to the original file (intended when the file is later
# going to be modified).

## "Global" list of files to divert
divert_files_list: []
# divert_files_list:
#   - original: '/bin/ls'
#     diverted: '/bin/ls_org'
#     copy: yes
#     # state: 'absent'
#   - original: '/usr/share/X11/xkb/symbols/de'
#     state: 'absent'
#     force: yes

## "Host group" list of files to divert
divert_files_group_list: []

## "Host" list of files to divert
divert_files_host_list: []

diverted_files_default_suffix: '.dpkg-orig'
```

List of internal variables used by the role:

    divert_files_list_combined


### Authors and license

`divert` role was written by:

- [Robin Schneider](https://github.com/ypid) | [e-mail](mailto:ypid@riseup.net)

License: [AGPLv3](https://tldrlegal.com/license/gnu-affero-general-public-license-v3-%28agpl-3.0%29)

***

README generated by [Ansigenome](https://github.com/nickjj/ansigenome/).
