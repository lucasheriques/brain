Run this to install Rosetta: 
`/usr/sbin/softwareupdate --install-rosetta --agree-to-license**`

Run this to install Xcode CLT:
`xcode-select --install` 

Install iTerm. Make Rosetta version of iTerm.

Run this to install Homebrew:
`/bin/bash -c "$(curl -fsSL [https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh](https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh))"`

Open iTerm Rosetta. Run the same command to install brew again.

Install Oh My Zsh:
`sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

Oh My Zsh plugins: spaceship, zsh-autosuggestions, zsh-syntax-highlighting.

Change zsh theme to spaceship

Create alises for brew (in ~/.zshrc):


alias zshconfig="code ~/.zshrc"
alias ohmyzsh="code ~/.oh-my-zsh"
alias brewr="arch -x86_64 /usr/local/bin/brew $@"
alias leg="arch -x86_64 $@"



Install fnm (node version manager)

Install Chrome and VS Code using Homebrew:


Install Raycast, MeetingBar, AppCleaner, JetBrains Toolbox, Discord, Slack, Kap, Obsidian

Setup SSH key on Mac and GitHub

Install fzf, use plugin on Oh My Zsh