# VS Code (code-server) on Binder Example

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/aculich/binder-vscode/main?urlpath=vscode/home/jovyan/hello_world_vscode.ipynb)
*(Click the badge above to launch!)*

This repository demonstrates how to run VS Code (via `code-server`) directly within a Binder environment using the `jupyter-vscode-proxy` extension.

The Binder link is specially configured to **launch directly into the VS Code interface and automatically open the `hello_world_vscode.ipynb` notebook** for editing.

## How it Works

* The `binder/` directory contains the configuration files for BinderHub.
* `binder/requirements.txt`: Specifies the necessary Python packages:
    * `jupyterlab`: Provides the base Jupyter environment.
    * `jupyter-vscode-proxy`: Installs the Jupyter server extension that manages and proxies `code-server`. It typically handles downloading `code-server` automatically if needed.
* The launch URL includes the parameter `?urlpath=vscode/home/jovyan/hello_world_vscode.ipynb`:
    * `vscode/`: Tells `jupyter-server-proxy` to route to the VS Code service managed by `jupyter-vscode-proxy`.
    * `/home/jovyan/hello_world_vscode.ipynb`: Specifies the path *within the container* to the file that VS Code should open on startup. Binder clones the repository into `/home/jovyan/`.

## What to Expect on Launch

1.  Click the "launch binder" badge above.
2.  BinderHub will build the Docker image based on the configuration files (this might take a few minutes the first time).
3.  Once the environment is ready, your browser will be redirected.
4.  **First Launch Delay:** The *very first time* `code-server` is started in a fresh Binder container, `jupyter-vscode-proxy` might need to download it. This can take 1-2 minutes. You might see a loading screen or messages indicating this download.
5.  After any necessary setup, the VS Code interface will load in your browser.
6.  The `hello_world_vscode.ipynb` notebook file will be open and ready for viewing or editing directly within VS Code.

You can use the integrated VS Code terminal, file explorer, editor, and other features just as you would locally, but operating on the files within your temporary Binder container.

## Files

* `binder/requirements.txt`: Python dependencies for Binder.
* `hello_world_vscode.ipynb`: A sample Jupyter Notebook intended to be opened in VS Code via the proxy.
* `README.md`: This file.