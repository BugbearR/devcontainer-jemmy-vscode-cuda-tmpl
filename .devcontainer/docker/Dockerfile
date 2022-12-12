FROM mcr.microsoft.com/devcontainers/base:jammy

USER root
RUN apt-get update -y \
    && DEBIAN_FRONTEND=noninteractive apt-get upgrade -y \
    && wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin \
    && mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600 \
    && wget https://developer.download.nvidia.com/compute/cuda/12.0.0/local_installers/cuda-repo-wsl-ubuntu-12-0-local_12.0.0-1_amd64.deb \
    && dpkg -i cuda-repo-wsl-ubuntu-12-0-local_12.0.0-1_amd64.deb \
    && cp /var/cuda-repo-wsl-ubuntu-12-0-local/cuda-*-keyring.gpg /usr/share/keyrings/ \
    && apt-get update -y \
    && sudo apt-get -y install cuda \
    && apt-get clean \
    && rm -rf /var/cache/apt/* /var/lib/apt/lists/

USER vscode
RUN mkdir -m 700 ~/.xdg

CMD [ "/bin/bash" ]
