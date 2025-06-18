# Building and Deploying the ChitChat

This guide will help you build and deploy the ChitChat project. The command-line tool `dfx` can be used to build and deploy the project to the mainnet.

## Local Development Setup

To set up the project for local development, follow these steps:

1. Install the required dependencies:
   - [Node.js](https://nodejs.org/)
   - [Rust](https://www.rust-lang.org/tools/install)
   - [DFX](https://internetcomputer.org/docs/building-apps/developer-tools/dfx/install)
   - [Docker](https://www.docker.com/products/docker-desktop)

2. Clone the repository and navigate to the project directory.

3. Start the local development environment:
   ```bash
   dfx start --clean --background
   ```

4. Deploy the canisters:
   ```bash
   dfx deploy
   ```

## Development Container Setup

For a consistent development environment, you can use the provided Dev Container:

1. Install [VS Code](https://code.visualstudio.com/) and the [Dev Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)

> Note that local development ports (e.g. the ports used by `dfx` or `vite`) are forwarded from the Dev Container to your local machine. In the VS code terminal, use Ctrl/Cmd+Click on the displayed local URLs to open them in your browser. To view the current port mappings, click the "Ports" tab in the VS Code terminal window.

### 2. Create a local developer identity.

To manage your project's canisters, it is recommended that you create a local [developer identity](https://internetcomputer.org/docs/building-apps/getting-started/identities) rather than use the `dfx` default identity that is not stored securely.

To create a new identity, run the commands:

```

dfx start --background

dfx identity new IDENTITY_NAME

dfx identity use IDENTITY_NAME

```

Replace `IDENTITY_NAME` with your preferred identity name. The first command `dfx start --background` starts the local `dfx` processes, then `dfx identity new` will create a new identity and return your identity's seed phase. Be sure to save this in a safe, secure location.

The third command `dfx identity use` will tell `dfx` to use your new identity as the active identity. Any canister smart contracts created after running `dfx identity use` will be owned and controlled by the active identity.

Your identity will have a principal ID associated with it. Principal IDs are used to identify different entities on ICP, such as users and canisters.

[Learn more about ICP developer identities](https://internetcomputer.org/docs/building-apps/getting-started/identities).

### 3. Deploy the project locally.

Deploy your project to your local developer environment with:

```
npm install
dfx deploy

```

Your project will be hosted on your local machine. The local canister URLs for your project will be shown in the terminal window as output of the `dfx deploy` command. You can open these URLs in your web browser to view the local instance of your project.

### 4. Obtain cycles.

To deploy your project to the mainnet for long-term public accessibility, first you will need [cycles](https://internetcomputer.org/docs/building-apps/getting-started/tokens-and-cycles). Cycles are used to pay for the resources your project uses on the mainnet, such as storage and compute.

> This cost model is known as ICP's [reverse gas model](https://internetcomputer.org/docs/building-apps/essentials/gas-cost), where developers pay for their project's gas fees rather than users pay for their own gas fees. This model provides an enhanced end user experience since they do not need to hold tokens or sign transactions when using a dapp deployed on ICP.

> Learn how much a project may cost by using the [pricing calculator](https://internetcomputer.org/docs/building-apps/essentials/cost-estimations-and-examples).

Cycles can be obtained through [converting ICP tokens into cycles using `dfx`](https://internetcomputer.org/docs/building-apps/developer-tools/dfx/dfx-cycles#dfx-cycles-convert).

### 5. Deploy to the mainnet.

Once you have cycles, run the command:

```

dfx deploy --network ic

```

After your project has been deployed to the mainnet, it will continuously require cycles to pay for the resources it uses. You will need to [top up](https://internetcomputer.org/docs/building-apps/canister-management/topping-up) your project's canisters or set up automatic cycles management through a service such as [CycleOps](https://cycleops.dev/).

> If your project's canisters run out of cycles, they will be removed from the network.

