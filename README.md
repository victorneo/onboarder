# Onboarder

Get your macOS device ready for work, fast.

Designed for teams to quickly get their team members up to speed with Day-1
productivity, or for you to repeatedly install the same set of software that
you need as quickly as possible on a new macOS device.

## Quickstart

First, you need a configuration file that specifies what software needs to be
installed and what shell script run. This configuration file can be hosted on
a Git repo, provided that it can be accessed via HTTP by the macOS device
running Onboarder.

Next, run the single-line command to install Onboarder and point it to where
your configuration file is (either locally or via HTTP).

## How It Works

Internally, Onboarder uses [Homebrew][1] and [Homebrew Cask][2] to install the
software that you need.

Configuration files are YAML files that allows you to specify what needs to be
installed via homebrew or homebrew-cask, as well as shell commands to run.


## Example Configuration File

The following configuration file does the following:
1. Installs `vim` via Homebrew
2. Clones a vim repository locally
3. Soft-links the config file from the repo to `~/.vimrc`
4. Runs a command to install all plugins using `vim-plug`

```
install-vim:
- install: vim
- run: git clone <repo-url> .vim
- run: ln -s .vimrc ~/.vim/.vimrc
- run: vim +'PlugInstall --sync' +qa
```

## License

Copyright 2019 Victor Neo

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.


[1]: https://brew.sh/
[2]: https://github.com/Homebrew/homebrew-cask
