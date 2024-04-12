# Tasks


- [x] 1 Language and Fonts 
- [x] 2 Pacman Mirror
- [x] 3 utils: gcc/make/cmake/jdk21/rust...
- [x] 4 paru Aur Sorce
- [x] 5 Lightweight Apps: paru, warp 
- [x] 6 Input Method
- [x] 7 Gaint Weight Apps: Web Borwser 
- [ ] 
- [ ] 
- [ ] 
- [ ] 
- [ ] 
- [ ] 上的上面行不行啊？反正输入法也只是用来玩儿的。我真的服了，这个傻逼输入法，为什么不能用 rime 呢？我真的感觉这样很疯狂，他妈的个傻逼东西


## 1 Language and Fonts

Install "JetBrainsMono-FiraMono-MiSans" fonts collections:

```sh
sudo cp -t $Path-To-Fonts /usr/share/fonts/
```

Refresh system font-cache

```sh
sudo fc-cache -f -v
```

Change font by `gnome-tweaks`. Succeed!



## 2 Pacman Mirrors

Normally it was configured on install Linux.

If not, add `Server = https://mirrors.ustc.edu.cn/..../$repo/$arch` to `/etc/pacman.d/mirrorlist`.

The succeed!



## 3 basic utils

Check your base versions firstly.

And then install:
```sh
sudo pacman -Syu --needed gcc make cmake git
```

Configure ssh and git config:

```sh
ssh-keygen -t rsa -C ABdeegl
```

Then add details:

```sh
user.name=ABdeeglr
user.email=abdeeglr@icloud.com
init.defaultbranch=main
gui.encoding=utf-8
i18n.commitencoding=utf-8
svn.pathnameencoding=utf-8
core.quotepath=false
```

At last, transmit ssh-key to the github.

Succeed!

## 4 Aur Source and paru builder.

**4.1 Build rustup and mirror configuration**

Firstly add ENV: 

```sh
export RUSTUP_DIST_SERVER=https://mirrors.ustc.edu.cn/rust-static
export RUSTUP_UPDATE_ROOT=https://mirrors.ustc.edu.cn/rust-static/rustup
```
or add them to `bash_profile` for current user.

Then install `rustup` and rust-toolchain:

```sh
sudo pacman -Syu --needed rustup
rustup default stable
```

and add `$CARGO_HOME` as `$HOME/.cargo`, create `cargo` mirror config by:


excute

```sh
export CAGO_HOME=$HOME/.cargo
```

and go into `.cargo` and `touch config`, at last add the content:

```txt
[source.crates-io]
replace-with = 'ustc'

[source.ustc]
registry = "git://mirrors.ustc.edu.cn/crates.io-index/"
```

**4.2 Install paru**

Clone paru git repo and build:

```sh
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```

## 5 Light Weight Apps: warp, obsidian, openssh-server, ...

Update pacman package database: `sudo pacman -Su`
Update paru package database: `paru -Syu`.

The run: `sudo pacman -S --needed tree tldr zsh`

Use `sudo systemctl start(&& enable) sshd` to start openssh service.


Install warp: Download the official *.pkg.tar.zst package. And then install locally by pacman:
```sh
sudo pacman -U {package}.pkg.tar.zst
```

Install Magic Software, and then install `oh-my-zsh`:

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

and add extensions:

```sh
cd ~/.oh-my-zsh/plugins
git clone git@github.com:zsh-users/zsh-autosuggestions.git
git clone git@github.com:zsh-users/zsh-syntax-highlighting.git
```

## 6 Input method

Install rime(input method framework) with fcitx5: 

```sh
sai fcitx5-rime fcitx5-chinese-addons
```

Configuration:

Writting below into the `/etc/environment`:

```sh 
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
SDL_IM_MODULE=fcitx
```


## 7 Gaint Weight Apps: Edge, Chrome, 


**Install Edge and chrome**

```sh
paru -S microsoft-edge-stable-bin
paru -S google-chrome
```

Restart machine before open them.





