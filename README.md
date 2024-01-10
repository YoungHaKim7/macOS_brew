# macOS_brew

- brew파일 편하게 어떤 컴퓨터에서든 설치한번에 다 하기
  - https://gist.github.com/ChristopherA/a579274536aab36ea9966f301ff14f3f

- Homebrew로 macOS  개발 환경 세팅 자동화
  - https://labs.brandi.co.kr/2020/05/26/leekh.html


# Installing Brew

Compete details are at Brew but fairly simple to install. Open terminal.app (command-space + "terminal") and paste this command on the command line.

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

If you don't have a recent version of macOS, you may need to install the latest Xcode command tools first. I don't like downloading all of Xcode, so I use this trick to only install the latest command-line tools.

```
touch /tmp/.com.apple.dt.CommandLineTools.installondemand.in-progress;
softwareupdate -i -a
rm /tmp/.com.apple.dt.CommandLineTools.installondemand.in-progress
```

Another easy way to install all of this, along with some good basic security hardening practices, is to use Mike McQuaid's Strap tool by going to https://macos-strap.herokuapp.com/. If you have a github account, it will also install basic github permissions.
Basic Brew Bundle

# The most basic command

```
brew bundle install
```

Looks for ~/Brewfile and installs its contents
Install a specific brewfile

If you want to use a brewfile from a non-standard place.

```
brew bundle --file=~/.private/Brewfile
```

Or more specifically:

```
brew bundle install --file=rs-brew-dump
```

Creating a Brewfile

You can dump a Brewfile of your current brew/cask/mas entries into your current directory with

```
brew bundle dump
```

or to a specific directory and file name.

```
brew bundle dump --file=~/.private/Brewfile
```

If a Brewfile already exists, you'll need to do

```
brew bundle dump --force
```

Cleaning up to match brewfile

If you want your current system configuration to match your brewfile

```
brew bundle --force cleanup
```
  