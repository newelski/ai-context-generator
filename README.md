# AI Context Generator

**What it does**: Scans your codebase and generates a structured, token-optimized summary containing your project's most important files, configurations, and code patterns.

**How it works**: Intelligently prioritizes critical config files (full content), summarizes source code by extracting key functions and imports, and skips irrelevant files like build artifacts and dependencies.

**Why you need it**: When working with AI assistants that have context limits, manually copying and pasting files is tedious and inefficient. `aic` automatically creates the optimal context for your specific project, saving time and ensuring nothing important gets missed.

## Installation

1. Download the `aic` script
2. Make it executable: `chmod +x aic`
3. Place in your PATH or run directly: `./aic`

**Requirements**: Python 3.6+
## Quick Start

```bash
# Basic usage - analyze current directory
./aic .

# Estimate project size before generating context  
./aic --estimate-size ./my-project

# Output to stdout for piping
./aic --stdout ./my-project | pbcopy

# Customize token limit
./aic --max-tokens 20000 ./large-project
```

## Usage

```bash
aic [-h] [-o OUTPUT] [--max-tokens MAX_TOKENS] [--stdout] [--estimate-size] directory

positional arguments:
  directory             Directory to scan (required)

options:
  -h, --help            Show help message
  -o OUTPUT, --output OUTPUT
                        Output file (default: smart_context.txt)
  --max-tokens MAX_TOKENS
                        Maximum tokens to generate (default: 15000)
  --stdout              Output to stdout instead of file
  --estimate-size       Estimate project size without generating context
```

## Supported Languages & Frameworks

**Languages**: Python, JavaScript, TypeScript, PHP, HTML, CSS, Java, C/C++, Go, Rust, Ruby, Swift, Kotlin

**Auto-detected Frameworks**: React, Vue.js, Svelte, Node.js

**Configuration Files**: package.json, requirements.txt, composer.json, Cargo.toml, tsconfig.json, and more
