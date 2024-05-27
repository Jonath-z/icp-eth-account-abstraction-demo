# ICP-Ethereum-Account-Abstraction

This basic boilerplate demonstrates how to create an Ethereum wallet using an ICP Principal or canister ID with Azle. It is inspired by the [`ethers_base example`](https://github.com/demergent-labs/azle/tree/main/examples/ethers_base).

Please remember that Azle is in beta and thus it may have unknown security vulnerabilities due to the following:

- Azle is built with various software packages that have not yet reached maturity
- Azle does not yet have multiple independent security reviews/audits
- Azle does not yet have many live, successful, continuously operating applications deployed to ICP

## Installation

> Windows is only supported through a Linux virtual environment of some kind, such as [WSL](https://learn.microsoft.com/en-us/windows/wsl/install)

On Ubuntu/WSL:

```bash
sudo apt-get install podman
```

On Mac:

```bash
brew install podman
```

It's recommended to use nvm and Node.js 20:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```

Restart your terminal and then run:

```bash
nvm install 20
```

Check that the installation went smoothly by looking for clean output from the following command:

```bash
node --version
```

Install the dfx command line tools for managing ICP applications:

```bash
DFX_VERSION=0.18.0 sh -ci "$(curl -fsSL https://sdk.dfinity.org/install.sh)"
```

Check that the installation went smoothly by looking for clean output from the following command:

```bash
dfx --version
```

If after trying to run `dfx --version` you encounter an error such as `dfx: command not found`, you might need to add `$HOME/bin` to your path. Here's an example of doing this in your `.bashrc`:

```bash
echo 'export PATH="$PATH:$HOME/bin"' >> "$HOME/.bashrc"
```

## Deployment

```bash
npm install

dfx start --clean --host 127.0.0.1:8000
```

```bash
AZLE_AUTORELOAD=true dfx deploy
```

To obtain your application's [canisterId]:

```bash
dfx canister id backend
```

Communicate with your canister using any HTTP client library, for example using `curl`:

```bash
curl http://[canisterId].localhost:8000/db
curl -X POST -H "Content-Type: application/json" -d "{ \"hello\": \"world\" }" http://[canisterId].localhost:8000/db/update
```

## Examples

There are many Azle examples in the [examples directory](https://github.com/demergent-labs/azle/tree/main/examples).
