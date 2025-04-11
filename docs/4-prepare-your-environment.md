# Prepare Your Environment

## Installing Node.js

In all projects 22nd version of Node.js is used, to be able to run them install the latest LTS (Long Term Support) version of Node.

If you have `nvm` installed, just run the following command:

```sh
nvm install --lts
```

In case if your platform is Linux or macOS and you don't have `nvm` installed use following commands:

```sh
# Download and install nvm:
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.2/install.sh | bash

# in lieu of restarting the shell
\. "$HOME/.nvm/nvm.sh"

nvm install --lts
```

If your platform is Windows, follow the [official installation guide](https://nodejs.org/en/download) from Node.js documentation.

## Installing pnpm

According of some objective reasons, such as packages installation speed, instead of `npm` as a package manager for all projects `pnpm` is used.

To install it run the following command:

```sh
corepack enable pnpm
```

## Setting up development environment

You can learn how set up a local development environment for running the app in [Expo's official docs](https://docs.expo.dev/get-started/set-up-your-environment/?platform=android&device=physical&mode=expo-go)

## Cloning a repo

For clonning repo just execute the following command:

```sh
git clone https://github.com/GatherFlow/client
```

## Installing dependencies

```sh
pnpm i
```

## Running the project


```sh
node --run dev
```