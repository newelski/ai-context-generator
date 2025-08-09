
# AI Context Generator

### Analyze a project and create a _single-file_ AI context prompt.
*I created this when I didn't have access to a CLI or IDE to read files and had to paste project details into Claude/ChatGPT web chat.*

![](https://img.shields.io/badge/python-3.6-orange) ![](https://img.shields.io/badge/vibe-coding-blue) ![](https://img.shields.io/badge/Claude-Opus_4.1-eeeeee)
![](https://img.shields.io/badge/version-1.3.37-green)
## Installation

1. Download the `aic` script
2. Make it executable: `chmod +x aic`
3. Place in your PATH or run directly: `./aic`

**Requirements**: Python 3.6+

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

## Example Output

See [full context prompt example](https://github.com/newelski/ai-context-generator/blob/main/smart_context.txt) or just `--estimate-size` of and exmple codebase ([tailwindcss](https://github.com/tailwindlabs/tailwindcss)):

```sh
============================================================
PROJECT SIZE ESTIMATION
============================================================
Directory: ./tailwindcss
Total files found: 520
Total disk size: 5MB

Estimated context tokens: ~79,097.0
Estimated context size: ~309KB
⚠️  Estimated size (79,097.0) exceeds limit (15,000)
   Consider increasing --max-tokens or the script will truncate content

BREAKDOWN:
Critical config files: 68 files
  └─ Total size: 50KB
     • packages/tailwindcss/package.json (4KB)
     • crates/node/package.json (2KB)
     • package.json (2KB)
     • packages/@tailwindcss-standalone/package.json (2KB)
     • README.md (2KB)
     • ... and 63 more

Important source files: 351 files (will be summarized)
  └─ .css: 17 files, 26KB
  └─ .html: 3 files, 28KB
  └─ .js: 8 files, 5KB
  └─ .rs: 54 files, 599KB
  └─ .ts: 263 files, 1MB
  └─ .tsx: 6 files, 2KB

Ignored files: 25 files
  └─ Total size: 2MB (skipped)
     • packages/tailwindcss/src/utilities.test.ts (754KB)
     • packages/tailwindcss/src/index.test.ts (136KB)
     • packages/tailwindcss/src/compat/plugin-api.test.ts (114KB)

Other files: 76 files (listed only)

============================================================
```
## Summary

**Why you need it**: When working with AI assistants that have context limits, manually copying and pasting files is tedious and inefficient. `aic` automatically creates the optimal context for your specific project, saving time and ensuring nothing important gets missed.

**What it does**: Scans your codebase and generates a structured, token-optimized summary containing your project's most important files, configurations, and code patterns.

**How it works**: Intelligently prioritizes critical config files (full content), summarizes source code by extracting key functions and imports, and skips irrelevant files like build artifacts and dependencies.

## Supported Languages & Frameworks

**Languages**: Python, JavaScript, TypeScript, PHP, HTML, CSS, Java, C/C++, Go, Rust, Ruby, Swift, Kotlin

**Auto-detected Frameworks**: React, Vue.js, Svelte, Node.js

**Configuration Files**: package.json, requirements.txt, composer.json, Cargo.toml, tsconfig.json, and more
