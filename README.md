# rpcsx-ui

This repo houses an experimental cross-platform UI for RPCSX built using Tauri and Svelte. UI is rendered using OS native browser frameworks, and IPC with the main RPCSX process will be done through the Rust backend.


---

## Table of Contents
- [Overview](#overview)
- [Requirements](#requirements)
    - [Windows](#windows)
    - [Linux](#linux)
    - [macOS](#macos)
- [Build & Run](#build--run)
- [Contributing](#contributing)
- [Recommended IDE Setup](#recommended-ide-setup)

---

## Overview

- **rpcsx-ui** is a Tauri + Svelte application designed to be a front-end for the [RPCSX](https://github.com/RPCSX/rpcsx) emulator.
- The front-end leverages:
    - **Rust** for the main Tauri process (and future IPC with RPCSX).
    - **Bun** as the JavaScript runtime and package manager.
    - **Svelte** for the UI layer in the Tauri webview.

---

## Requirements

You’ll need both **Rust** (with Cargo) and **Bun** installed. See below for platform-specific instructions.
- [Rust](https://www.rust-lang.org/tools/install)
- [Bun](https://bun.sh/)

### Windows


1. **Install Rust**
    - Download and run the official [Rustup installer](https://rustup.rs/).
    - Once installed, verify by running in **PowerShell** or **Command Prompt**:
      ```bash
      rustc --version
      cargo --version
      ```

2. **Install Build Tools**
    - You need the Microsoft C++ build tools for linking native crates:
        - If you have **Visual Studio** installed, you likely already have these.
        - Otherwise, install [Build Tools for Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio).

3. **Install Bun**
    - Download from [Bun.sh](https://bun.sh/) and follow the Windows instructions.
    - Verify:
      ```bash
      bun --version
      ```

4. **(Optional) WSL**
    - If you prefer developing in **WSL** (Ubuntu, etc.), follow the [Linux](#linux) steps below within your WSL shell.
    - Make sure you also install Rust and Bun in WSL (not just in Windows).


### Linux

> Instructions below assume **Ubuntu 22.04** or similar. Adjust packages as needed for other distributions.
1. **Install Rust**
   ```bash
   curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
   source $HOME/.cargo/env
   rustc --version
   cargo --version
    ```

2. **Install Bun**
- Follow the instructions on the [Bun website](https://bun.sh/docs/installation).
    - Verify:
      ```bash
      bun --version
      ```
   
3. **Install Dependencies**
- For Ubuntu 22.04:
    ```sh
    sudo apt update
    sudo apt-get install -y libwebkit2gtk-4.1-dev libappindicator3-dev librsvg2-dev patchelf
    ```
4. (Optional) Additional Packages
    - If you're on a different distro or older Ubuntu release, you may need:
        - `libwebkit2gtk-4.0-dev`
        - `libgtk-3-dev`
        - `pkg-config`


### macOS
1. Install Xcode Command Line Tools:
    ```sh   
    xcode-select --install
    ```
   
2. Install Rust:
    ```sh
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
    source $HOME/.cargo/env
    rustc --version
    cargo --version
    ```
   
3. Install Bun:
    - Follow the instructions on the [Bun website](https://bun.sh/docs/installation).
    - Verify the installation:
        ```sh
        bun --version
        ```
      
4. WebKit / Tauri
    - macOS has WebKit already, so typically you don’t need an extra package for Tauri to build, but if you run into issues, you can install it via Homebrew:
        ```sh
        brew install webkit2gtk
        ```
    - If you encounter build errors, ensure you have the latest Xcode or Command Line Tools installed.



## Build & Run

1. Clone the repository:
    ```sh
    git clone https://github.com/RPCSX/rpcsx-ui.git
    cd rpcsx-ui
    ```

2. Install dependencies:
    ```sh
    bun install
    ```

3. Run Tauri in development mode:
    ```sh
    bun run tauri dev
    ```
    This launches the Tauri development server, which will open a window with the UI. Any changes you make to the code will automatically refresh the window.

4. Build a release-ready bundle:
    ```sh
    bun run tauri build
    ```

## Contributing
We welcome contributions! Here are the basic steps:

1. Fork and clone this repository.

2. Create a new branch for your fix or feature:
`git checkout -b feature/make-game-go-brrr`

3. Make your changes, ensuring they pass any linting or formatting checks.

4. Test locally:

  - Run the dev server (`bun run tauri dev`) and confirm the UI changes work.
  - If relevant, build for production (`bun run tauri build`) and do a quick functional check.

5. Commit and push your branch, then open a Pull Request.

## Build Guide

- `bun install`
- `bun run tauri dev`

## Recommended IDE Setup

[VS Code](https://code.visualstudio.com/) with the following extensions:
- [Svelte](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode)
- [Tauri](https://marketplace.visualstudio.com/items?itemName=tauri-apps.tauri-vscode)
- [Tailwind CSS](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)
- [rust-analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer)
