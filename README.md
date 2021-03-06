# copr-rebuild-tools

This repository contains tools for launching mass rebuilds of packages in [Copr](http://copr.fedoraproject.org/) build service.

## Features
- [x] Multiple [backends](#backends) for various programming langues package managers
- [x] Submiting all packages from given backend
    - [x] Limitable
    - [x] Possibility to specify the last submited package and continue from following one
- [x] Possibility to submit only new packages (or only new versions of packages)
- [x] Possibility to rebuild only given set of packages
- [x] Statistics of success rate


## Backends

| Name     | Key         | URL                                                                 |
| -------- | ----------- | ------------------------------------------------------------------- |
| PyPI     | `pypi`      | [pypi.python.org](https://pypi.python.org)                          |
| RubyGems | `rubygems`  | [rubygems.org](http://rubygems.org)                                 |
| Tito     | `tito`      | [github.com/dgoodwin/tito](https://github.com/dgoodwin/tito)        |

You are welcome to write your own backend. Please see a [guide](backends/README.md) describing how to do it.

## Configuration

See [config](/config) directory for examples.


## Usage

    copr-rebuild -c <config> <backend> <action>

See [configuration](#configuration) and [backends](#backends) sections. Also see `--help` for possible actions.

Examples:

    copr-rebuild -c config/vagrant.ini rubygems submit --new-packages
    copr-rebuild -c config/vagrant.ini rubygems submit --previous foo --limit 100
    copr-rebuild -c ~/config.ini pypi stats
    copr-rebuild -c ~/config.ini pypi successful
