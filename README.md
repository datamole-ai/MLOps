# ML DevOps Assignment (Infrastructure part)

## Story
Recently, you joined a company doing projects in the data science field and now you have to kick off the platform for their projects.

People there are familiar with Python, Jupyter, and Kubernetes. The company also has quite powerful hardware that you can utilize for this purpose.

As you need to present your idea to others, you decide to prepare a proof of concept.

## Assignment

### Idea

Run k3s (https://k3s.io/) on the company's bare metal HW and launch JupyterHub (https://github.com/jupyterhub/zero-to-jupyterhub-k8s) with custom Jupyter image as backend per each data scientist. The custom Jupyter image should be built on top of the existing minimal Jupyter notebook (https://hub.docker.com/r/jupyter/minimal-notebook) and extended by installing pandas and dvc.

### The simplification for this assignment
You should know what you are doing and what are the consequences but generally, you don’t need to worry about the parts mentioned below. They are not crucial for the assignment, but you should be ready for questions on these topics.

- If it’s running as root or as another user.
- Mounting storages.
- HTTPS, certificates.
- Ingress, node ports, load balancer, and other network stuff.
- LDAP, SSO, AD integration.

### Guide

- Install multipass (https://multipass.run/) on your laptop.
- Spin-off two virtual machines.
- Install k3s on these machines -- one master, two slaves in total.
- Use existing Helm charts to deploy JupyterHub.
  - There you will need to modify the configuration -- create a few example users, etc.
- Create your own custom version of the Jupyter image (mentioned in the Idea), that will be available in the deployed JupyterHub.

### Test suite
- Open the web browser and go to IP/DN of the running JupyterHub services.
- Log in as an example user, eg. user1/user1.
- Be able to choose your custom Jupyter image with a few extra python packages.
- Be able to create a notebook, use added Python packages, save notebook, log out.
- Be able to repeat the steps above for a user2.

### Notes
- Ubuntu is preferred.
- You will need to have and be able to use `docker`, `helm`, `kubectl`, `multipass`, `k3`.
  - `Lens` (https://k8slens.dev/) could be handy for you.
