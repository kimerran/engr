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
engr --glm                    # GLM coding plan (z.ai)
engr --kimi                   # Kimi provider (Moonshot)
engr --openrouter             # OpenRouter provider
engr --openai                 # OpenAI provider
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

### GLM coding plan (z.ai)

Requires a z.ai API key:

```bash
export ENGR_ZAI_API_KEY="your-key"
engr --glm
```

### Kimi (Moonshot)

Requires a Moonshot API key:

```bash
export ENGR_KIMI_API_KEY="your-key"
engr --kimi
```

Uses the `kimi-k2.5` model on `api.moonshot.ai`.

### OpenRouter

Requires an API key:

```bash
export ENGR_OPENROUTER_API_KEY="your-key"
engr --openrouter
```

Uses the OpenRouter SDK compatibility layer to route calls through the Claude API at `https://api.anthropic.com/v1/`.

### OpenAI

Requires an API key:

```bash
export ENGR_OPENAI_API_KEY="your-key"
engr --openai
```

Uses the OpenAI SDK compatibility layer to route calls through the Claude API at `https://api.anthropic.com/v1/`.

## Help

```bash
engr --help
```