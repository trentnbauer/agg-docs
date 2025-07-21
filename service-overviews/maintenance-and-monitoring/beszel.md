# Beszel

[Link to App](https://beszel.xfgn.dev/)

[Link to GitHub or Website](https://beszel.dev/)

Beszel is a lightweight server monitoring platform that includes Docker statistics, historical data, and alert functions.

It has a friendly web interface, simple configuration, and is ready to use out of the box. It supports automatic backup, multi-user, OAuth authentication, and API access.

Beszel is hosted on Espresso

### Web UI / Server

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/main/docker-compose/beszel.yml" %}

### Agent

This agent is deployed to all hosts via the ['all' Portainer Stack](../portainer-and-gitops/all-compose-stacks.md)&#x20;

### Agent with GPU monitoring (Nvidia)

{% @github-files/github-code-block url="https://github.com/trentnbauer/agg/blob/main/docker-compose/beszel-agent-gpu.yml" %}
