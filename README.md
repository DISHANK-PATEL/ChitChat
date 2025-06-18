# ChitChat

The ChitChat example demonstrates how an ICP smart contract can be used to interact with a large language model (LLM) to generate text. The user can input a prompt, and the smart contract will use the LLM to generate a response.
The response is then returned to the user, and the user can submit some follow-up prompts to continue the conversation.

This example uses Rust, the primary programming language for developing canisters on ICP.

## Deployment Instructions

To deploy this project to the mainnet, follow these steps:

1. Clone this repository
2. Install the required dependencies
3. Follow the deployment steps in BUILD.md

## Local Development

To develop this project locally, follow these steps:

1. Clone this repository
2. Install the required dependencies
3. Follow the development setup steps in BUILD.md

## Project structure

```
src/
├── llm_chatbot/
│   ├── src/
│   │   └── lib.rs
│   └── Cargo.toml
└── llm_chatbot_assets/
    ├── src/
    │   └── index.html
    └── package.json
```

## Setting up Ollama

To be able to test the agent locally, you'll need a server for processing the agent's prompts. For that, we'll use `ollama`, which is a tool that can download and serve LLMs.
See the documentation on the [Ollama website](https://ollama.com/) to install it. Once it's installed, run:

```
ollama serve
# Expected to start listening on port 11434
```

The above command will start the Ollama server, so that it can process requests by the agent. Additionally, and in a separate window, run the following command to download the LLM that will be used by the agent:

```
ollama run llama3.1:8b
```

The above command will download an 8B parameter model, which is around 4GiB. Once the command executes and the model is loaded, you can terminate it. You won't need to do this step again.

For more detailed instructions, please refer to the `BUILD.md` file.
