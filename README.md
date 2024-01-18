# 👋🏻 Welcome, Sponsor! ❤️

- [👋🏻 Welcome, Sponsor! ❤️](#-welcome-sponsor-️)
- [🙋‍♂️ What is this?](#️-what-is-this)
- [How do I use this?](#how-do-i-use-this)
  - [Docker Swarm + Ansible (automatically) 🐳 + 🦾](#docker-swarm--ansible-automatically---)
  - [Kubernetes (Helm Charts) ⎈](#kubernetes-helm-charts-)
  - [Docker Swarm Manually (the old way) 👴🏻](#docker-swarm-manually-the-old-way-)
- [FAQ](#faq)
  - [Where to go for help?](#where-to-go-for-help)
  - [How do I request a recipe?](#how-do-i-request-a-recipe)
  - [Can I contribute fixes etc?](#can-i-contribute-fixes-etc)
  - [Bootstrap flux](#bootstrap-flux)

# 🙋‍♂️ What is this?

This is the premium version of [Funky Penguin's Geek Cookbook](https://geek-cookbook.funkypenguin.co.nz). 

The repository includes:
* Standard docker-compose files for each recipe in the cookbook
* Ansible playbooks for automatically deploying the entire stack plus popular/current recipes
* Helm charts for deploying various recipes into Kubernetes (WIP)

# How do I use this?

## Docker Swarm + Ansible (automatically) 🐳 + 🦾 

Detailed instructions are available [here](https://geek-cookbook.funkypenguin.co.nz/premix/ansible/operation/).

## Kubernetes (Helm Charts) ⎈ 

1. Create a [GitHub Personal Access Token](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line), with repository access
2. Add a helm repository by running: 
```
export PAT=<YOUR PERSONAL ACCESS TOKEN>
helm repo add geek-cookbook-premix https://$PAT@raw.githubusercontent.com/funkypenguin/geek-cookbook-premix/helm-charts/
helm repo update
```

Example output:
```
# helm search repo geek-cookbook-premix
NAME                                   	CHART VERSION	APP VERSION	DESCRIPTION
geek-cookbook-premix/autopirate        	0.1.0        	1.16.0     	A Helm chart for Kubernetes, crafted by the fin...
geek-cookbook-premix/autopirate-storage	0.1.2        	1.16.0     	A Helm chart for Kubernetes, crafted by the fin...
geek-cookbook-premix/funkycore         	1.0.0        	1.0.0      	A collection of helpers for all Cookbook Charts
geek-cookbook-premix/huginn            	0.1.0        	1.16.0     	A Helm chart for Kubernetes
geek-cookbook-premix/wash-hands        	0.0.3        	0.0.1      	Some base dependencies in a sane cluster
```

3. Run `helm search repo geek-cookbook-premix` to see the shiny

## Docker Swarm Manually (the old way) 👴🏻

1. At a high level, ```git pull git@github.com:funkypenguin/geek-cookbook-premix.git /var/data/config```.
2. For each recipe, edit the .yml and replace my config (data paths, `example.com` domain name, etc) with yours
3. Where a ```<recipe name>.env-sample``` exists, rename this to ```<recipe-name>.env```, and customize


# FAQ

## Where to go for help?

1. The [Discord chat](http://chat.funkypenguin.co.nz) for realtime (*but non-persistent*) support
2. The [Discourse forums](https://discourse.geek-kitchen.funkypenguin.co.nz/), to trawl through previous support/discussions

## How do I request a recipe?

Create an issue, a template is waiting to help you identify the required details

## Can I contribute fixes etc?

Of course! Submit a PR, we'll go from there!

## Bootstrap flux

Create personal token at https://github.com/settings/tokens, Create a GitHub personal access token that can create repositories by checking all permissions under repo, as well as all options under admin:public_key

Save the token to your ansible vault, as github_flux_token