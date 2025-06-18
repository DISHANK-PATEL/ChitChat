![image](https://github.com/user-attachments/assets/d00f9889-0746-4c96-872b-fadab53419f9)

## ChitChat The Decentralised Chatbot

The Project is End‑to‑end decentralized chatbot platform comprising a Rust canister backend, an ICP(Internet Computer Protocol)asset canister for frontend delivery, and a local Ollama server for LLM inference.

Project runs directly on IC nodes within a subnet — a set of decentralized machines run by independent node providers across the globe.

Rust codebase is compiled to WebAssembly for on‑chain execution, managing chat state, candid interfaces, and HTTP‑out calls.

Frontend (HTML5, Tailwind CSS, vanilla JS,Vite) lives in its own asset canister, served globally via the ICP HTTP gateway.

Ollama integration runs an 8B‑parameter Llama3 model off‑chain on localhost:11434, delivering streamed AI responses back into the canister.

## Usecase Diagram

![image](https://github.com/user-attachments/assets/fddf2443-0817-4acd-97eb-389596bcbfb8)

##  Architecture 
The Internet Computer (ICP) uses a novel hybrid architecture that combines elements of Proof of Stake with advanced cryptographic techniques to achieve scalability and decentralization. Here's a breakdown of the sense (economic logic) and the consensus mechanism:

Utility Token (ICP):
ICP tokens are used to power computation (converted into “cycles”), incentivize node providers, and participate in governance.

Staking via Neurons (NNS):
Users lock ICP tokens into neurons within the Network Nervous System (NNS) to vote on governance proposals.
This is not used for block validation, but it regulates the network: upgrades, node provider onboarding, etc.

## Consensus Mechanism
The Internet Computer uses a four-layer consensus model. Nodes are authenticated via the NNS to prevent Sybil attacks. A random beacon using threshold BLS signatures selects the block-making committee. Selected nodes propose blocks through threshold relay. Finalization is achieved using a BFT protocol similar to HotStuff, ensuring fast and secure block notarization.

## Screenshots
![image](https://github.com/user-attachments/assets/b9792cbb-90da-4aac-9d7b-f15211071f26)

![image](https://github.com/user-attachments/assets/5e8681ca-563a-450a-8b97-00ec374bc510)

ICP.Ninja: Browser-based IDE for ICP canisters: A fully in-browser development environment allowing you to write, compile, and deploy Motoko and Rust canisters without installing dfx 
Allows Seamless deployment: Deploys canisters (frontend and backend) directly to ICP mainnet from the browser—with URLs valid for 20 minutes (redeployable for extended use)

![image](https://github.com/user-attachments/assets/55ca6493-b82e-44d1-9edd-c40eeb8bc473)
Candid UI is for testing Web3 smart contracts (canisters) on ICP.Its like Postmans Web3 equivalent

![image](https://github.com/user-attachments/assets/59368e54-dfcd-4e66-94c9-5caffa8cadee)

![image](https://github.com/user-attachments/assets/90661613-186d-41d2-b0b3-2792f07ab7ad)
Mainnet Deployment details





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
