# Embedded Linux Kitchen

## Task 1: Configure a Toolchain Using crosstool-NG

This repository contains a guide to configure a custom toolchain using crosstool-NG for embedded Linux development.

### Overview

crosstool-NG is a versatile tool that helps in building cross-compilation toolchains for various architectures. This guide outlines the steps to configure and build a toolchain tailored for embedded Linux development.

### Prerequisites

1. **Host System**: A Linux-based environment (Ubuntu, Fedora, etc.)
2. **Required Packages**:
   - `gcc`, `g++`
   - `make`
   - `gawk`
   - `bison`
   - `flex`
   - `texinfo`
   - `libncurses5-dev`
   - `libz-dev`
   - `git`
3. **crosstool-NG**: Install the latest version from the official repository.

### Installation Steps

1. Clone the crosstool-NG repository:
   ```bash
   git clone https://github.com/crosstool-ng/crosstool-ng.git
   cd crosstool-ng
   ./bootstrap
   ./configure --enable-local
   make
   make install
   ```

2. Create a workspace directory for the toolchain:
   ```bash
   mkdir -p ~/ct-ng-workspace
   cd ~/ct-ng-workspace
   ```

3. Initialize the configuration:
   ```bash
   ct-ng menuconfig
   ```
   - Select the target architecture (e.g., `arm-shikka-linux-gnueabihf`).
   - Configure other options like C library, kernel headers, and debug options.

4. Save and exit the configuration menu.

5. Build the toolchain:
   ```bash
   ct-ng build
   ```

   The toolchain will be built in the `~/x-tools/` directory by default.

### Verifying the Toolchain

1. Add the toolchain binaries to the `PATH`:
   ```bash
   export PATH="~/x-tools/arm-shikka-linux-gnueabihf/bin:$PATH"
   ```

2. Verify the toolchain:
   ```bash
   arm-shikka-linux-gnueabihf-gcc --version
   ```


