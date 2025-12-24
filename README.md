Hi Mary! To get the demo running, please try the following steps. I'm assuming you'll be using your Mac:


1. Get a copy of this repository. If you're reading this on Github, you've at least logged in, because currently this is a private repository. To be able to clone it, I recommend downloading a ZIP file (via the green "Code" button at the top right) and then un-zipping it into a folder of your choice.

2. Install `uv` from [Astral's website](https://docs.astral.sh/uv/getting-started/installation/#__tabbed_1_1).
This is a modern Python package manager---it's magic for managing (i.e. not having to deal with figuring out) dependencies.

3. Open two terminals, and navigate to the folder where this file is and start the web server by running:
  - In the first terminal, start a Jupyter server with the command below. This server will run any notebook backends, and will probably automatically open a page in your default browser
    ```bash
    uvx --with-requirements=requirements.in --from=jupyter-core --with=jupyterlab jupyter lab --IdentityProvider.token=512ac78f14e1141db1fac17e8b4099c1e5bc7d589518b38c --ServerApp.allow_origin='http://localhost:3000' --port=8888`
    ```
  - In another terminal, start Myst with `uvx --from=mystmd myst start`. This starts the page rendering server, but doesn't always open up a page automatically. This command might prompt you to install NodeJS, which is a javascript backend, if you do not already have it installed.
  - In your browser, type `http://localhost:3000` to look at the interactive paper.

