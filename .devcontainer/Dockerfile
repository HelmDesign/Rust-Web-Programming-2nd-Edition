FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        build-essential \
        ca-certificates \
        curl \
        git \
        gnupg \
        lsb-release \
        python3 \
        python3-pip \
        python3-venv \
        nodejs \
        npm \
        docker.io \
        docker-compose-plugin \
        unzip \
    && rm -rf /var/lib/apt/lists/* \
    && curl -fsSL https://sh.rustup.rs | sh -s -- -y --profile minimal \
    && mkdir -p /tmp/terraform \
    && curl -fsSL https://releases.hashicorp.com/terraform/1.9.8/terraform_1.9.8_linux_amd64.zip -o /tmp/terraform.zip \
    && unzip -o /tmp/terraform.zip -d /tmp/terraform \
    && install -m 0755 /tmp/terraform/terraform /usr/local/bin/terraform \
    && rm -rf /tmp/terraform /tmp/terraform.zip

ENV PATH="/home/vscode/.cargo/bin:${PATH}"

USER vscode

RUN rustup component add rustfmt clippy
