## ChitChat The Decentralised Chatbot

The Project is End‑to‑end decentralized chatbot platform comprising a Rust canister backend, an ICP asset canister for frontend delivery, and a local Ollama server for LLM inference.

Rust codebase is compiled to WebAssembly for on‑chain execution, managing chat state, candid interfaces, and HTTP‑out calls.

Frontend (HTML5, Tailwind CSS, vanilla JS) lives in its own asset canister, served globally via the ICP HTTP gateway.

Ollama integration runs an 8B‑parameter Llama3 model off‑chain on localhost:11434, delivering streamed AI responses back into the canister.

Full project tooling includes Cargo for the canister, npm for asset bundling, and BUILD.md–driven workflows for local development and mainnet deployment.

## Deployment Instructions

To deploy this project to the mainnet, follow these steps:

1. Clone this repository
2. Install the required dependencies
3. Follow the deployment steps in BUILD.md

## Local Development

```bash
# 1. Start Ollama server
ollama serve

# 2. Run Ollama model
ollama run llama3.1:8b

# 3. Start local Internet Computer
dfx start --background

# 4. Frontend setup
cd src/llm_chatbot_assets
npm install
npm run dev

# 5. Backend (canister) setup
cd ../llm_chatbot
cargo build --target wasm32-unknown-unknown --release
dfx --version
dfx identity use default
dfx deploy

# 6. Open the app
# Visit in browser:
# http://127.0.0.1:8000
````

## Mainnet Deployment

```bash
# 1. Create & select a new identity
dfx identity new <IDENTITY_NAME>
dfx identity use <IDENTITY_NAME>

# 2. Redeem cycles from faucet
dfx cycles redeem-faucet-coupon COUPON --ic

# 3. Deploy to ICP mainnet
dfx deploy --ic

# 4. Access the live app
# URL printed by deploy, e.g.:
# https://<your-canister-id>.ic0.app
```

---

For deeper configuration and build workflows, see [BUILD.md](./BUILD.md).

```
```
