ARG VARIANT="buster"
FROM mcr.microsoft.com/vscode/devcontainers/rust:0-${VARIANT}

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive

# update rustup toolchain & add components
RUN su vscode -c 'rm /usr/local/cargo/bin/rustfmt /usr/local/cargo/bin/cargo-fmt'
RUN su vscode -c 'rustup default stable'
RUN su vscode -c 'rustup component add clippy rustfmt'
RUN su vscode -c 'rustup update'

# generate completions
RUN su vscode -c 'mkdir ~/.zfunc'
RUN su vscode -c 'rustup completions zsh > ~/.zfunc/_rustup'
RUN su vscode -c 'rustup completions zsh cargo > ~/.zfunc/_cargo'

# load completions via .zshrc
RUN su vscode -c 'echo fpath+=~/.zfunc >> ~/.zshrc'
RUN su vscode -c 'echo autoload -U compinit >> ~/.zshrc'
RUN su vscode -c 'echo compinit -i >> ~/.zshrc'
