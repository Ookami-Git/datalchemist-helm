FROM mcr.microsoft.com/devcontainers/go:1-1.22-bookworm

# Helm
RUN curl -fsSL https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# kubectl (pour helm qui en a besoin)
RUN curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" \
    && install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl \
    && rm kubectl

RUN rm -f /etc/apt/sources.list.d/yarn.list \
    && apt-get update && apt-get install -y git \
    && rm -rf /var/lib/apt/lists/*

# Autocomplétion Helm + kubectl
RUN echo 'source <(helm completion bash)' >> /home/vscode/.bashrc \
    && echo 'source <(kubectl completion bash)' >> /home/vscode/.bashrc