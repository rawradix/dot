# Bootstrapping Mac as Developer Machine

## Install https://brew.sh

- `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

- Follow the instructions in the terminal:

After completion for me it was

```bash
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/r/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

### Install a good terminal

For me that's kitty:

```bash
brew install kitty
```

Viable alternatives: iTerm2 is popular. The built-in Terminal ain't too bad.

### Install your favorite shell

That's `zsh` for me.

```bash
brew install zsh
```

Viable alternatives: Stick with bash. Use fish.

### Customize zsh a bit

I like zapzsh by chris@machine

```bash
zsh <(curl -s https://raw.githubusercontent.com/zap-zsh/zap/master/install.zsh) --branch release-v1
```

### Install a low-battery requiring browser

That's a tough one. I'm going for Kagi's Orion browser.

```bash
brew install --cask orion
```

Orion can be configured a bit
    - Right-Click on top bar -> `Use Compact Size`
    - Settings
        - Appearance:
            - `Show tabs:` -> `On the Side`
            - `Auto-show sidebar in full screen`
        - Browsing:
            - `Automatic HTTPS upgrade`
            - `Show full website address`
            - `Use tab switcher UI for Ctrl + Tab`
            - `Check spelling while typing`
        - Privacy
            - `Remove history items` -> `Manually`
        - Search
            - `Search engine` -> `DuckDuckGo`
            - Autocomplete everything
        - Extensions
            - Enable a bunch of them

and qutebrowser.

```bash
brew install qutebrowser
```

Viable alternatives: Brave.

Set it up:
	- Automatically keep Orion up to date
	- Taps on the side
	- DuckDuckGo as default search engine

### macOS sane usability setup

- Remap keys to correct/used position

```bash
brew install --cask karabiner-elements
```

Then remap things.

    - tilde to pinkie

- A good clipboard manager

```bash
brew install clipy
```

This will probably install Rosetta (translate Intel to Apple's own silicon). If not, you can install it:

```bash
softwareupdate --install-rosetta
```

- Install some decent fonts

```bash
brew tap homebrew/cask-fonts
```

Search for your favorites, mine are:

```bash
brew install --cask font-caskaydia-cove-nerd-font
brew install --cask font-victor-mono-nerd-font
```

- Now we can configure kitty:

```bash
mkdir ~/.conf/kitty
```

- In case you want to stream

```bash
brew install --cask obs
```

- Alternative to spotlight

First we need to unmark all the searchlocations for the indexer of spotlight in the settings. By now, you'll figure this out.

Then

```bash
brew install raycast
```

- Window snapping

```bash
brew install rectangle
```

- macOS does not understand the difference between Trackpad & Mouse scrolling

Get

https://pilotmoon.com/scrollreverser/

- Easy Move and Resize

```bashbash
brew install --cask easy-move-plus-resize
```

- Remap keys to match your muscle memory

My muscle memory comes from Linux (KDE) / Fedora.

- External Displays

This is a downer: https://support.apple.com/en-us/HT213503
I still can't believe they have these weird requirements on external displays...

- Watch videos

```bash
brew install vlc
```
## Programming Languages

### Go Lang

It is possible to use the https://go.dev way. However, I make use of brew:

```bash
brew install go
```

We set the `GOPATH` to a better location:

```bash
export GOPATH=$HOME/.local/share/go
export PATH=$HOME/.local/share/go/bin:$PATH
```

### Rust

```bash
brew install rust
```

Add the above to your `.***rc` file. For me it is two additional lines in my `.zshrc`.

Remove the regular location if it was created:

```bash
sudo rm -rf ~/go
```

- Getting productive in the shell
    - [x] zsh
    - [x] lunarvim config
    - [x] doing
    - [ ] tmux + plugins based on conf
        - especially pomo plugin
        - alias note=`lvim ~/Repos/github.com/rawradix/log/$(isosec).md`  # ~zettelkasten

```bash
brew install lsd
brew install lynx
brew install marksman
brew install zoxide
brew install tree
brew install tig
```

Zoxide needs to initialized in zsh. See: https://github.com/ajeetdsouza/zoxide.

> dd this to the end of your config file (usually `~/.zshrc`):

> `eval "$(zoxide init zsh)"`
> For completions to work, the above line must be added after compinit is called. You may have to rebuild your completions cache by running rm ~/.zcompdump*; compinit.

## Project management and focus help

```bash
brew install brew-gem
brew gem install doing
```

See: https://github.com/ttscoff/doing/wiki/Installation


## Shell based development environment

### TL;DR;

```bash
brew install tldr
tldr --update  # updates/fetches the commands DB
```

### Neovim

```bash
brew install neovim
```

and an ide-ish good default called lunarvim.org

It comes with a set of requirements

Now lunarvim itself:

```bash
LV_BRANCH='release-1.3/neovim-0.9' bash <(curl -s https://raw.githubusercontent.com/LunarVim/LunarVim/release-1.3/neovim-0.9/utils/installer/install.sh)
```

