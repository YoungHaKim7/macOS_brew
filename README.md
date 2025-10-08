# link

- [#rust개발-관련macOS fix문제해결](#rust개발-관련)

<hr />

- 결제한 어플
  - [ScreenBrush](https://apps.apple.com/kr/app/screenbrush/id1233965871?l=en-GB&mt=12)
  - [Movist](https://apps.apple.com/kr/app/movist/id461788075?l=en-GB&mt=12)

<hr>


# brew update & upgrade

```bash
brew update && brew upgrade
```

# brew doctor

```bash
brew update-reset && brew update
brew doctor
```

- brew 관리 
  - https://elsainmac.tistory.com/889

```
brew autoremove
```

# alacritty (macOS) 

- malware해결하는법
```bash
brew install --cask alacritty --no-quarantine
```

- https://github.com/alacritty/alacritty/issues/4673#issuecomment-771291615

# m1 install rosetta2

- https://www.macobserver.com/tips/how-to/install-rosetta-2-on-apple-silicon-macs-m1-m2-and-m3/

<hr>


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

# homebrew에 설치 되어 있다 확인 

```
$ find /opt/homebrew -name "*asio*" -type d 2>/dev/null | head -10
  ⎿  /opt/homebrew/Cellar/boost/1.89.0/include/boost/asio
     /opt/homebrew/Cellar/asio
     /opt/homebrew/Cellar/asio/1.36.0/include/asio
     /opt/homebrew/Cellar/asio/1.36.0/share/asio

# fd
fd -g '*asio*' | head -10
```

- fd 사용법
  - https://inpa.tistory.com/entry/Modern-Linux-%F0%9F%90%A7-fd-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%82%AC%EC%9A%A9%EB%B2%95-find-%EB%8C%80%EC%8B%A0-%EC%9D%B4%EA%B1%B0-%EC%93%B0%EC%9E%90

# 에러나는거 따로 alacritty

```
brew install --cask alacritty --no-quarantine
```
- https://github.com/alacritty/alacritty/issues/4673#issuecomment-771291615

# The most basic command

```
brew bundle install
```

Looks for ~/Brewfile and installs its contents
Install a specific brewfile

If you want to use a brewfile from a non-standard place.
- 난 이걸로 함. 파일 만들어 주고 실행하면 바로 설치 진행됨.
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
  
# M1 한/영 키 세팅 다시 ₩~ 백틱

- 맥북M1pro_한국인_개발자를 위한 키보드 세팅!_한영키딜레이_해결&백틱(backtick,grave)한영구분없이_백틱키(backtick key)타이핑되게하기 | GlobalYoung
  -  https://youtu.be/8aTi_hIFbQQ?si=6-D0rKJ8gzFCdFTt
  - [MAC] BackTick( ` ) 으로 고정시키기 https://kimbangg.tistory.com/m/315

- [Mac] 맥북에서 Caps Lock 으로 한/영 전환 설정/해제

  -  http://heyo.net/wp/67388
  -  https://info-jella.tistory.com/entry/%EB%A7%A5%EB%A7%A5%EB%B6%81-%EC%B4%88-%EA%B0%84%EB%8B%A8-%EB%8C%80%EB%AC%B8%EC%9E%90-%EB%B3%80%ED%99%98%EB%B0%A9%EB%B2%95-%EC%98%81%EB%AC%B8%EB%B3%80%ED%99%98-%EB%B0%A9%EB%B2%95

<hr>

# Rust개발 관련

# 에러 해결 모음

- 'xcrun: error: unable to find utility "metal", not a developer tool or in PATH' error when compiling 'gfx-backend-metal' #2309 

- Install Xcode from the Apple App Store.
- Install the command line tools with xcode-select --install. This might do nothing on your machine.
- If `xcode-select --print-path prints /Library/Developer/CommandLineTools…`
- then run `sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer`.

  - 해결 출처 : https://github.com/gfx-rs/gfx/issues/2309

```bash
==> git-lfs
Update your git config to finish installation:

  # Update global git config
  $ git lfs install

  # Update system git config
  $ git lfs install --system

fish completions have been installed to:
  /opt/homebrew/share/fish/vendor_completions.d
==> uv
fish completions have been installed to:
  /opt/homebrew/share/fish/vendor_completions.d
==> pnpm
pnpm requires a Node installation to function. You can install one with:
  brew install node

fish completions have been installed to:
  /opt/homebrew/share/fish/vendor_completions.d
```

- 250719


```bash
CLANG_CONFIG_FILE_SYSTEM_DIR: /opt/homebrew/etc/clang
CLANG_CONFIG_FILE_USER_DIR:   ~/.config/clang

LLD is now provided in a separate formula:
  brew install lld

Using `clang`, `clang++`, etc., requires a CLT installation at `/Library/Developer/CommandLineTools`.
If you don't want to install the CLT, you can write appropriate configuration files pointing to your
SDK at ~/.config/clang.

To use the bundled libunwind please use the following LDFLAGS:
  LDFLAGS="-L/opt/homebrew/opt/llvm/lib/unwind -lunwind"

To use the bundled libc++ please use the following LDFLAGS:
  LDFLAGS="-L/opt/homebrew/opt/llvm/lib/c++ -L/opt/homebrew/opt/llvm/lib/unwind -lunwind"

NOTE: You probably want to use the libunwind and libc++ provided by macOS unless you know what you're doing.

llvm is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have llvm first in your PATH, run:
  fish_add_path /opt/homebrew/opt/llvm/bin

For compilers to find llvm you may need to set:
  set -gx LDFLAGS "-L/opt/homebrew/opt/llvm/lib"
  set -gx CPPFLAGS "-I/opt/homebrew/opt/llvm/include"
==> pnpm
```

- 250823 업데이트 하고 체크

```bash
Removing: /Users/gy-gyoung/Library/Caches/Homebrew/ruff_bottle_manifest--0.12.7... (8.3KB)
Removing: /Users/gy-gyoung/Library/Caches/Homebrew/ruff--0.12.7... (12.9MB)
==> No outdated dependents to upgrade!
==> Caveats
fish completions have been installed to:
  /opt/homebrew/share/fish/vendor_completions.d
Emacs Lisp files have been installed to:
  /opt/homebrew/share/emacs/site-lisp/cmake
==> libpq
libpq is keg-only, which means it was not symlinked into /opt/homebrew,
because it conflicts with PostgreSQL.

If you need to have libpq first in your PATH, run:
  fish_add_path /opt/homebrew/opt/libpq/bin

For compilers to find libpq you may need to set:
  set -gx LDFLAGS "-L/opt/homebrew/opt/libpq/lib"
  set -gx CPPFLAGS "-I/opt/homebrew/opt/libpq/include"

For pkg-config to find libpq you may need to set:
  set -gx PKG_CONFIG_PATH "/opt/homebrew/opt/libpq/lib/pkgconfig"
==> cmake
To install the CMake documentation, run:
  brew install cmake-docs
==> pnpm
pnpm requires a Node installation to function. You can install one with:
  brew install node
==> tabby
Please note tabby expects to read its configuration file from
/Users/gy-gyoung/.tabby/config.toml

For more information see https://tabby.tabbyml.com/docs/administration/model/

For a list of the available models see https://tabby.tabbyml.com/docs/models/

To start tabbyml/tabby/tabby now and restart at login:
  brew services start tabbyml/tabby/tabby
Or, if you don't want/need a background service you can just run:
  /opt/homebrew/opt/tabby/bin/tabby serve --device metal
```

- 250525 업데이트 하고 체크

```bash

 libpq
libpq is keg-only, which means it was not symlinked into /opt/homebrew,
because conflicts with postgres formula.

If you need to have libpq first in your PATH, run:
  fish_add_path /opt/homebrew/opt/libpq/bin

For compilers to find libpq you may need to set:
  set -gx LDFLAGS "-L/opt/homebrew/opt/libpq/lib"
  set -gx CPPFLAGS "-I/opt/homebrew/opt/libpq/include"

For pkg-config to find libpq you may need to set:
  set -gx PKG_CONFIG_PATH "/opt/homebrew/opt/libpq/lib/pkgconfig"
==> llvm
CLANG_CONFIG_FILE_SYSTEM_DIR: /opt/homebrew/etc/clang
CLANG_CONFIG_FILE_USER_DIR:   ~/.config/clang

LLD is now provided in a separate formula:
  brew install lld

Using `clang`, `clang++`, etc., requires a CLT installation at `/Library/Developer/CommandLineTools`.
If you don't want to install the CLT, you can write appropriate configuration files pointing to your
SDK at ~/.config/clang.

To use the bundled libunwind please use the following LDFLAGS:
  LDFLAGS="-L/opt/homebrew/opt/llvm/lib/unwind -lunwind"

To use the bundled libc++ please use the following LDFLAGS:
  LDFLAGS="-L/opt/homebrew/opt/llvm/lib/c++ -L/opt/homebrew/opt/llvm/lib/unwind -lunwind"

NOTE: You probably want to use the libunwind and libc++ provided by macOS unless you know what you're doing.

llvm is keg-only, which means it was not symlinked into /opt/homebrew,
because macOS already provides this software and installing another version in
parallel can cause all kinds of trouble.

If you need to have llvm first in your PATH, run:
  fish_add_path /opt/homebrew/opt/llvm/bin

For compilers to find llvm you may need to set:
  set -gx LDFLAGS "-L/opt/homebrew/opt/llvm/lib"
  set -gx CPPFLAGS "-I/opt/homebrew/opt/llvm/include"
==> mas
fish completions have been installed to:
  /opt/homebrew/share/fish/vendor_completions.d
==> gh
fish completions have been installed to:
  /opt/homebrew/share/fish/vendor_completions.d
==> cmake
To install the CMake documentation, run:
  brew install cmake-docs

Emacs Lisp files have been installed to:
  /opt/homebrew/share/emacs/site-lisp/cmake
==> starship
fish completions have been installed to:
  /opt/homebrew/share/fish/vendor_completions.d
==> pnpm
pnpm requires a Node installation to function. You can install one with:
  brew install node

fish completions have been installed to:
  /opt/homebrew/share/fish/vendor_completions.d
==> uv
fish completions have been installed to:
  /opt/homebrew/share/fish/vendor_completions.d
==> pip-tools
fish completions have been installed to:
  /opt/homebrew/share/fish/vendor_completions.d
==> tabby
Please note tabby expects to read its configuration file from
/Users/gy-gyoung/.tabby/config.toml

For more information see https://tabby.tabbyml.com/docs/administration/model/

For a list of the available models see https://tabby.tabbyml.com/docs/models/

To start tabbyml/tabby/tabby now and restart at login:
  brew services start tabbyml/tabby/tabby
Or, if you don't want/need a background service you can just run:
  /opt/homebrew/opt/tabby/bin/tabby serve --device metal
==> Updating Homebrew...
Already up-to-date.

```

<hr />

# macOS 화면보호기 실행 안되게 계속 깨어있게 하기(caffeine)
- Utility that prevents the system from going to sleep

```
brew install --cask caffeine
```

# rosetta update

```
 softwareupdate --install-rosetta --agree-to-license
```

```
# arm에서 x86실행하는 방법 먼저 로제타 설치해야함
$ arch -x86_64 zsh

$ softwareupdate --install-rosetta --agree-to-license
```
