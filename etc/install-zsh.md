# MAC OS에 ZSH 설치하기

## Brew 설치

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

## ZSH 설치

brew를 통한 zsh 설치 (업그레이드)

```
brew install zsh
```

## oh-my-zsh 설치

```
curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh
```

ZSH를 기본으로 사용하도록 설정
```
chsh -s /usr/local/bin/zsh
```

## ZSH 테마 설정

```
vim ~/.zshrc
```

테마 변경
```
ZSH_THEME="agnoster"
```
테마 다운로드
[http://iterm2colorschemes.com/](http://iterm2colorschemes.com/)

프로파일 접근
```
cmd + ,
```

import theme하여 내려받은 테마 설정
```
terminal > Solarized Dark.termianl
```

## 폰트 설정하기

폰트 다운로드[https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf](https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf)

프로파일에서 폰트 설정

## 쉘 네임 지우기

~/.zshrc에 코드 추가
```
prompt_context() {
  if [[ "$USER" != "$DEFAULT_USER" || -n "$SSH_CLIENT" ]]; then
    prompt_segment black default "%(!.%{%F{yellow}%}.)$USER"
  fi
}
```

## 레퍼런스
- [https://thdev.tech/mac/2016/05/01/Mac-ZSH-Install.html](https://thdev.tech/mac/2016/05/01/Mac-ZSH-Install.html)
- [https://wayhome25.github.io/etc/2017/03/12/zsh-alias/](https://wayhome25.github.io/etc/2017/03/12/zsh-alias/)