FROM mcr.microsoft.com/devcontainers/jekyll:2-bullseye

USER root

RUN mkdir -p /usr/local/bundle \
    && chown -R vscode:vscode /usr/local/bundle

USER vscode