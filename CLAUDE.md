# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a Vim plugin that provides syntax highlighting for Bazel's .bazelrc configuration files. The plugin follows standard Vim plugin structure and conventions.

## Project Structure

```
.
├── syntax/bazelrc.vim     # Main syntax highlighting definitions
└── ftdetect/bazelrc.vim   # File type detection for *.bazelrc files
```

## Syntax Highlighting Features

The syntax file (`syntax/bazelrc.vim`) supports:

- **Comments**: `#` comments with TODO/FIXME highlighting
- **Keywords**: `import` and `try-import` statements
- **Scopes**: Command scopes like `build:`, `test:config`, etc.
- **Config Groups**: The part after `:` in scope definitions
- **Options**: Both short flags (`-c`) and long options (`--enable_bzlmod`)

The syntax uses Vim's very magic regex (`\v`) for cleaner pattern matching and proper containment relationships between syntax elements.

## Key Syntax Patterns

- Scopes are matched at line start with `^[A-Za-z0-9_:]+`
- Config groups use contained matching within scopes
- Options use lookbehind assertions (`\s\@=`) to ensure proper whitespace context
- Comments can contain TODO/FIXME keywords for special highlighting

## File Type Detection

The plugin automatically detects files matching `*.bazelrc` pattern and applies the bazelrc syntax highlighting.

## Testing

The plugin includes comprehensive tests using vader.vim:

```
test/
├── fixtures/sample.bazelrc    # Test fixture with various syntax elements
├── vader/filetype.vader       # File type detection tests
├── vader/syntax.vader         # Syntax highlighting tests
└── run_tests                 # Test runner script
```

### Running Tests

```bash
# Run all tests (requires vader.vim)
./test/run_tests

# Install vader.vim if needed
git clone https://github.com/junegunn/vader.vim.git ~/.vim/pack/vendor/start/vader
```

### Test Coverage

- File type detection for various .bazelrc file patterns
- Syntax highlighting for all supported elements:
  - Comments and TODO/FIXME keywords  
  - Import statements (import, try-import)
  - Command scopes (build, test, run, etc.)
  - Configuration groups (build:debug, test:unit)
  - Options (short flags like -c, long options like --enable_bzlmod)

## Development Practices

- Use conventional commit syntax for git comments