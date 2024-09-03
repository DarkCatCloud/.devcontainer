FROM fedora:40

LABEL \
  version="1.0" \
  description="ay0ks' very own development-ready container" \
  maintainer="Dimitriy \"ay0ks\" <ay0o0ks000@gmail.com>" \
  repository="https://github.com/ay0ks/.devcontainer"

VOLUME ["/sys/fs/cgroup", "/var/run/docker.sock"]

RUN dnf upgrade -y
RUN dnf group install -y \
  "Fedora Server Edition" "Development and Creative Workstation"
RUN dnf group install -y \
  "Administration Tools" "C Development Tools and Libraries" \
  "Cloud Infrastructure" "Cloud Management Tools" "Container Management" \
  "D Development Tools and Libraries" "Development Tools" "Editors" \
  "Headless Management" "Network Servers" "RPM Development Tools" \
  "Security Lab" "System Tools" "Text-based Internet"
RUN dnf install -y dotnet-sdk-8.0 aspnetcore-runtime-8.0
RUN curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.rpm.sh | sudo bash
RUN dnf install -y zsh just fastfetch git-lfs
RUN dnf distro-sync -y
RUN dnf makecache -y
RUN git lfs install
RUN curl -sSL https://get.docker.com/ | sudo sh

USER root
RUN useradd -d /home/codespace -G wheel -m -s /usr/bin/zsh -U codespace
RUN echo "codespace:codespace" | chpasswd

USER codespace
WORKDIR /home/codespace
RUN git clone https://github.com/ohmyzsh/ohmyzsh.git ~/.oh-my-zsh
RUN cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc

RUN dotnet tool install --global x
RUN dotnet tool install --global dotnet-ef --version 8.0.8
RUN dotnet workload install aspire
