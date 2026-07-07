# Running this sample

This is the Rust solution for the LLM client sample. You need a Rust toolchain installed; see the [official install guide](https://www.rust-lang.org/tools/install).

The client calls a model through the GitHub Models inference endpoint (`https://models.github.ai/inference/chat`) and reads your token from the `OPENAI_API_KEY` environment variable.

## -0- Set your API key

```bash
# zsh/bash
export OPENAI_API_KEY="{{YOUR_GITHUB_TOKEN}}"
```

```powershell
# PowerShell
$env:OPENAI_API_KEY = "{{YOUR_GITHUB_TOKEN}}"
```

## -1- Build the sample

```bash
cargo build
```

## -2- Run the sample

```bash
cargo run
```

The client starts the calculator MCP server, lists its tools, and uses the model (`openai/gpt-5-mini`) to call the `add` tool. You should see output that lists the available tools and prints the result of the tool call.
