# link

- [#rust개발-관련macOS fix문제해결](#rust개발-관련)

<hr>


# brew update & upgrade

```bash
brew update && brew upgrade
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

<hr />

# macOS 화면보호기 실행 안되게 계속 깨어있게 하기(caffeine)
- Utility that prevents the system from going to sleep

```
brew install --cask caffeine
```
