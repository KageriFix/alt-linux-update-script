# Project Overview

This project provides a set of shell scripts for automating system updates, application installations, and other tasks on Alt Linux.

## `up` Script

The `up` script, designed to be run with root privileges, automates system maintenance.

### Key Features of `up`

- **System Updates:** It updates the system by running `epm -y ei` and `epm -y full-upgrade`.
- **Application Installation:** It can install `git`, `vscode`, and `yt-dlp`.
- **Command-Line Interface:** Supports `--install` (or `-i`) and `--help` (or `-h`).
- **Logging:** Provides clear, color-coded output for all operations.

## `yt` Script

The `yt` script is a wrapper around `yt-dlp` for downloading YouTube videos.

### Key Features of `yt`

- **Video Downloading:** Downloads a video from a given URL.
- **Cookie Authentication:** Requires a `cookies.txt` file in the user's home directory.
- **Formatting:** Recodes the video to `mp4`.
- **Organized Output:** Saves the video to `~/video/<uploader>/<title>.mp4`.

## `ai` Script for AI Tools

The project also includes an `ai` script that installs `nodejs` and `gemini-cli`.

# Building and Running

This project consists of standalone shell scripts and does not require a separate build process.

1.  **Make the scripts executable:**
    ```bash
    chmod +x up yt ai
    ```

2.  **(Optional but Recommended) Create symbolic links:**
    For global access, create symbolic links to a directory in your `PATH`.
    ```bash
    sudo ln -sf $(pwd)/up /usr/local/bin/up
    sudo ln -sf $(pwd)/yt /usr/local/bin/yt
    ```

3.  **Run the scripts:**
    ```bash
    # Update system and install apps
    sudo up --install

    # Download a video
    yt -u <URL>

    # Install AI tools
    ./ai
    ```

# Testing

There are no automated tests. To test functionality, run the scripts on an Alt Linux system and verify:

- `up` correctly runs system updates.
- `up --install` installs `git`, `vscode`, and `yt-dlp`.
- `yt` correctly downloads a video with the specified format and path.
- The scripts handle missing dependencies or arguments gracefully.

# Development Conventions

The scripts follow standard shell scripting best practices:

- **Error Handling:** `set -e` is used in the `up` script for immediate exit on error.
- **Functions:** Code is organized into functions with clear responsibilities.
- **Logging:** Scripts provide informative, color-coded output.
