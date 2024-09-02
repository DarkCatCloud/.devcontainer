FROM fedora:40

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
RUN dnf install -y zsh
RUN dnf distro-sync -y
RUN dnf makecache -y

USER root
RUN useradd -d /home/codespace -G wheel -m -s /usr/bin/zsh -U codespace
RUN echo "codespace:codespace" | chpasswd

USER codespace
RUN git clone https://github.com/ohmyzsh/ohmyzsh.git ~/.oh-my-zsh
RUN cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
RUN dotnet tool install --global x
RUN dotnet tool install --global dotnet-ef --version 8.0.8
