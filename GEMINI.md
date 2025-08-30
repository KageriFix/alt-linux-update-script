# Project Overview

This project provides a shell script for automating system updates and application installations on Alt Linux. The script, named `up`, is designed to be run with root privileges and offers the following key features:

- **System Updates:** It checks for and installs system updates using `apt-get` and `epm`, the default package managers in Alt Linux.
- **Application Installation:** It can install a predefined list of popular applications, including code editors (VSCode, Cursor) and other utilities.
- **Smart Checks:** The script intelligently checks if applications are already installed before attempting to install them, looking for executables in the system's PATH, package manager records, and symbolic links.
- **Flexible Installation:** It attempts to install applications using `epm play` first, and if that fails, it falls back to using `apt-get`.
- **Command-Line Interface:** The script supports command-line arguments like `--install` (or `-i`) to trigger the application installation process and `--help` (or `-h`) to display usage instructions.

The primary technologies used are **Bash scripting**, `epm`, and `apt-get`.

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

**Testing:**

There are no automated tests in this project. To test the script's functionality, you can run it on an Alt Linux system and verify the following:

*   The script correctly identifies and installs system updates.
*   The script correctly identifies and installs the specified applications.
*   The script correctly identifies already installed applications and skips them.

# Development Conventions

The script follows standard shell scripting best practices:

*   **Error Handling:** The `set -e` option is used to exit the script immediately if any command fails.
*   **Functions:** The code is organized into functions with clear responsibilities (e.g., `check_root`, `install_apps_if_missing`, `perform_upgrade`).
*   **Logging:** The script provides informative output with color-coded messages for success, warnings, and errors.
*   **Variable Naming:** Variables are named descriptively (e.g., `HAS_UPDATES`, `INSTALL_APPS`).
