# tljh-shared-directory

`tljh-shared-directory` is a plugin for [The Littlest JupyterHub (TLJH)](https://tljh.jupyter.org) which sets up a 'shared directory' for the Hub in `/srv/Shared_Data`.  The `/srv/Shared_Data` shared directory is used to 'publish' notebooks internally within the Hub.  E.g. if there are three users, then User A may develop a Notebook in their `/home/user_a` directory and when it is complete copy it to `/srv/Shared_Data` (symlinked in every user's home) so that User B and User C can see the Notebook.  However, only User A is able to make further changes to it.

Shared directories go hand-in-hand with Dashboarding apps like Voila or Panel.  User A copies a Notebook into the `/srv/Shared_Data` directory, then other users can view that Notebook as a Dashboard.

# Install

Include `--plugin tljh-shared-directory` in your TLJH install script.  An example install with admin user `admin` would be:

```
#!/bin/bash
curl https://raw.githubusercontent.com/jupyterhub/the-littlest-jupyterhub/master/bootstrap/bootstrap.py \
  | sudo python3 - \
    --admin admin --plugin git+https://github.com/magicsward/tljh-shared-directory
```
