FROM fedora:latest

RUN dnf upgrade -y
RUN dnf group install -y \
  "Fedora Server Edition" "Development and Creative Workstation"
RUN dnf group install -y \
  "Administration Tools" "C Development Tools and Libraries" \
  "Cloud Infrastructure" "Cloud Management Tools" "Container Management" \
  "D Development Tools and Libraries" "Development Tools" "Editors" \
  "Headless Management" "Network Servers" "RPM Development Tools" \
  "Security Lab" "System Tools" "Text-based Internet"
RUN dnf install dotnet-sdk-8.0 aspnetcore-runtime-8.0 -y 
RUN dnf distro-sync -y
RUN dnf makecache -y
RUN dotnet tool install --global x
RUN dotnet tool install --global dotnet-ef --version 8.0.8

COPY files/entry.sh /entry.sh
RUN chmod +x /entry.sh

ENTRYPOINT ["/entry.sh"]
