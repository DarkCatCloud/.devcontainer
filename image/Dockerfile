FROM fedora:40

LABEL \
  version="1.0" \
  description="ay0ks' very own development-ready container" \
  maintainer="Dimitriy \"ay0ks\" <ay0o0ks000@gmail.com>" \
  repository="https://github.com/ay0ks/.devcontainer"

RUN dnf upgrade -y
RUN dnf -y install systemd && dnf clean all && \
  (cd /lib/systemd/system/sysinit.target.wants/ ; for i in * ; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i ; done) ; \
  rm -f /lib/systemd/system/multi-user.target.wants/* ;\
  rm -f /etc/systemd/system/*.wants/* ;\
  rm -f /lib/systemd/system/local-fs.target.wants/* ; \
  rm -f /lib/systemd/system/sockets.target.wants/*udev* ; \
  rm -f /lib/systemd/system/sockets.target.wants/*initctl* ; \
  rm -f /lib/systemd/system/basic.target.wants/* ;\
  rm -f /lib/systemd/system/anaconda.target.wants/*

VOLUME ["/sys/fs/cgroup", "/var/run/docker.sock"]
CMD ["/sbin/init"]

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
