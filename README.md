# engr

Claude Code wrapper with provider switching. Run Claude Code against Anthropic (default), MiniMax, or Ollama without manual config changes.

## Install

```bash
./install
```

Installs to `~/.local/bin` by default. Pass a different path:

```bash
./install /usr/local/bin
```

If the install directory isn't in your PATH, the script will print the line to add to your shell config.

## Usage

```bash
engr                        # Anthropic (default)
engr --minimax              # MiniMax provider
engr --ollama               # Ollama provider
engr --ollama -m glm-5:cloud  # Ollama with model override
engr [any claude args]      # All other args pass through to claude
```

## Providers

### Anthropic (default)

No extra setup. Uses whatever Anthropic credentials are already configured.

### MiniMax

Requires an API key:

```bash
export ENGR_MINIMAX_API_KEY="your-key"
engr --minimax
```

### Ollama

Requires [Ollama](https://ollama.com) installed. The script auto-starts the Ollama server and pulls the model if not found locally.

```bash
engr --ollama                # Default model
engr --ollama -m glm-5:cloud # Specific model
```

## Help

```bash
engr --help
```