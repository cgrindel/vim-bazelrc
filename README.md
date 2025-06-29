# vim-bazelrc

A vim plugin that provides syntax highlighting for Bazel's .bazelrc files.

## Installation

### Using vim-plug

Add the following line to your `~/.vimrc` (or `~/.config/nvim/init.vim` for Neovim):

```vim
Plug 'cgrindel/vim-bazelrc'
```

Then run:

```
:PlugInstall
```

### Manual Installation

1. Download the plugin files
2. Copy `syntax/bazelrc.vim` to `~/.vim/syntax/`
3. Copy `ftdetect/bazelrc.vim` to `~/.vim/ftdetect/`

## Features

- Syntax highlighting for `.bazelrc` configuration files
- Automatic file type detection for `*.bazelrc` files
- Support for:
  - Comments with TODO/FIXME highlighting
  - Import statements (`import`, `try-import`)
  - Command scopes (`build:`, `test:`, etc.)
  - Configuration groups and options

## Usage

Once installed, the plugin will automatically apply syntax highlighting to any file with a
`.bazelrc` extension.
