# Project Overview

This project provides a shell script for automating system updates and basic application installations on Alt Linux. The script, named `up`, is designed to be run with root privileges.

## Key Features

- **System Updates:** It updates the system by running `epm -y ei` (to update package indexes) and `epm -y full-upgrade` (to perform the upgrade).
- **Application Installation:** It can install `git` and `vscode` (logged as `vscode`) using the `epm` package manager.
- **Command-Line Interface:** The script supports command-line arguments:
    - `--install` (or `-i`) to trigger the application installation process.
    - `--help` (or `-h`) to display usage instructions.
- **Logging:** Provides clear, color-coded output for all operations.

The primary technology used is **Bash scripting** with `epm`.

# Building and Running

This project is a standalone shell script and does not require a separate build process.

**To run the script:**

1.  **Make the script executable:**
    ```bash
    chmod +x up
    ```

2.  **Run with `sudo` for system updates:**
    ```bash
    sudo ./up
    ```

3.  **Run with the `--install` flag to also install applications:**
    ```bash
    sudo ./up --install
    ```

# `ai` Script for AI Tools

The project also includes an `ai` script that installs `nodejs` and `gemini-cli`.

## Usage

1.  **Make the script executable:**
    ```bash
    chmod +x ai
    ```

2.  **Run the script:**
    ```bash
    ./ai
    ```
The script will install `nvm` (Node Version Manager) to manage `nodejs` versions, the latest LTS version of `nodejs`, and `gemini-cli`.

# Testing

There are no automated tests in this project. To test the script's functionality, you can run it on an Alt Linux system and verify the following:

*   The script correctly runs the system update commands.
*   When run with `--install`, the script correctly installs `git` and `vscode`.
*   The script correctly identifies if `git` or `vscode` are already installed and attempts to update them.

# Development Conventions

The script follows standard shell scripting best practices:

*   **Error Handling:** The `set -e` option is used to exit the script immediately if any command fails.
*   **Functions:** The code is organized into functions with clear responsibilities (e.g., `check_root`, `install_applications`, `update_indexes`, `perform_full_upgrade`).
*   **Logging:** The script provides informative output with color-coded messages for success, warnings, and errors.