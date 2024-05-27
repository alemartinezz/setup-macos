# Setup

Setup guide for my macos

## Manual settings

1. Trackpad settings
	1. System Settings -> trackpad -> tap to click (ON)
	2. System Setting -> accessibility -> Pointer control -> Ignore built in trackpad when mouse or wireless trackpad is present (ON)
2. External monitor
	1. System settings -> Battery -> Options -> Prevent automatic sleeping on power adapter when the display is off (ON)


## CMD Configs

Show hidden files & folders
```shell
defaults write com.apple.Finder AppleShowAllFiles true && killall Finder
```

Default screenshots folder
```bash
mkdir -p ~/Desktop/Screenshots && defaults write com.apple.screencapture location ~/Desktop/Screenshots && killall SystemUIServer
```

Default screenshot format to jpg
```shell
defaults write com.apple.screencapture type jpg && killall SystemUIServer
```

Xcode and its developer tools
```bash
xcode-select --install
```

## Homebrew

1. Open up a terminal window and install homebrew with the following command:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. After installing, add it to the path (replace ”[username]” with your actual username). **Look at the output of the installation command.**
```bash
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/ale/.zprofile
```

```shell
eval "$(/opt/homebrew/bin/brew shellenv)"
```



## Terminal

**Requirements**
Homebrew, iTerm2 (Switch to iTerm2 for the remainder of this walkthrough.)

### Theme

#### Oh My Zsh
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

#### PowerLevel10K Theme for Oh My Zsh
```bash
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

```bash
vi ~/.zshrc
```

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

```bash
source ~/.zshrc
```

#### Meslo Nerd Font

Install the font by pressing “y” and then quit iTerm2.

#### Configure PowerLevel10K

Restart iTerm2. You should now be seeing the PowerLevel10K configuration process. If you don’t, run the following:
```bash
p10k configure
```


Follow the instructions for the PowerLevel10K configuration to make your terminal look as desired.

### Profile settings

Open iTerm2 Preferences: **Cmd** + **,** (comma) as a shortcut.

1. Font size
	1. Profiles > Text
	2. I increase my font size to about 14px
2. New window default size
	1. Go to Profiles > Window
	2. Mine is `165x45`
3. Keybindings
	1. Go to Profiles -> Keys -> Key mappings
	2. Jump left
		1. Left“Keyboard Shortcut”: Option + Left Arrow.  
		2. “Action”: Send Escape Sequence  
		3. In the input box that appears, type **b** (because the escape sequence for moving to the previous word in many shells like bash and zsh is **Esc-b**). 
	3. Jump right
		1. “Keyboard Shortcut”: Option + Right Arrow.  
		2. “Action”: Send Escape Sequence  
		3. In the input box that appears, type **f** (because the escape sequence for moving to the next word in many shells is **Esc-f**).
	4. Delete entire word while pressing Option
		1. “Action”: “Send Hex Code” or “Send Escape Sequence”
		2. “Send Hex Code”: **0x1b 0x08** or **0x17** (If “Send Hex Code” doesn’t work as expected, try “Send Escape Sequence”.)

### ZSH Plugins

1. zsh-autosuggestions:
```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

2. Install zsh-syntax-highlighting:
```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```


3. Open the ”~/.zshrc” file in your desired editor and modify the plugins line to what you see below.
```bash
vi ~/.zshrc
```

```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting web-search)
```

4. Load the new plugins
```bash
source ~/.zshrc
```


### ZSH Themes

#### SSH Key

1. Generate a new SSH key for secure authentication with GitHub.
```bash
mkdir -p ~/.ssh && ssh-keygen -t ed25519 -C "martinezcornes@icloud.com" -f ~/.ssh/personal_git && chmod 600 ~/.ssh/personal_git && chmod 600 ~/.ssh/personal_git.pub && cat ~/.ssh/personal_git.pub | pbcopy
```
2. Add the SSH key to your GitHub account under `Settings` -> `SSH and GPG Keys`.
3. Add your key to the SSH agent and test connectivity.
```bash
ssh-add ~/.ssh/personal_git
```
```bash
ssh -i ~/.ssh/personal_git -T git@github.com
```
```bash
ssh-keyscan -H github.com >> ~/.ssh/known_hosts
```

#### Download & Import themes
1. Clone themes repo
```bash
mkdir $HOME/Desktop/projects && cd $HOME/Desktop/projects && GIT_SSH_COMMAND="ssh -i ~/.ssh/personal_git -o IdentitiesOnly=yes" git clone git@github.com:alemartinezz/iterm-themes.git 
```
3. Open iTerm2 Preferences: **Cmd** + **,** (comma) as a shortcut.
4. Go to Profiles > Colors  
5. Import the downloaded color profile you want, or all.  
6. Select the color profile

You can find other themes here: Iterm2 Color Schemes [https://iterm2colorschemes.com/](https://iterm2colorschemes.com/)**)

## Programs

Misc
```bash
brew install --cask iterm2 && brew install --cask obsidian && brew install --cask visual-studio-code && brew install --cask whatsapp && brew install --cask chatgpt &&  brew install --cask notion
```

Rust w rustup
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

---

Incluir generacion de clave ssh para bajar temas
publicar esta guia publica y accesible
Cambiar color de titulo 3 y italic
Investigar que es zsh bien