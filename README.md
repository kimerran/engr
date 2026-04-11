# engr

[![CI](https://github.com/kimerran/engr/actions/workflows/ci.yml/badge.svg)](https://github.com/kimerran/engr/actions/workflows/ci.yml)

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
engr --litellm                # LiteLLM proxy
engr --bifrost                # MaximHQ Bifrost gateway
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

### LiteLLM

Requires [LiteLLM](https://github.com/BerriAI/litellm) proxy running. Set your API key and optionally the proxy URL:

```bash
export ENGR_LITELLM_API_KEY="your-master-key"
engr --litellm
```

Defaults to `http://localhost:4000`. Override with `ENGR_LITELLM_BASE_URL`:

```bash
export ENGR_LITELLM_BASE_URL="https://litellm.mycompany.com"
engr --litellm
```

Pass a model override:

```bash
engr --litellm -m gpt-4o
```

### MaximHQ Bifrost

Requires a Maxim workspace API key and Bifrost gateway URL:

```bash
export ENGR_BIFROST_API_KEY="maxim-xxxx"
export ENGR_BIFROST_BASE_URL="https://<your-workspace>.bifrost.getmaxim.ai"
engr --bifrost
```

Pass a model override:

```bash
engr --bifrost -m anthropic/claude-sonnet-4-5
```

## Help

```bash
engr --help
```