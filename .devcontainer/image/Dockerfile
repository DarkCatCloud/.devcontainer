FROM fedora:latest

RUN dnf upgrade -y
RUN dnf group list
RUN dnf install dotnet-sdk-8.0 aspnetcore-runtime-8.0 -y 
RUN dnf distro-sync -y
RUN dnf makecache -y
RUN dotnet tool install -g x ef

COPY files/entry.sh /entry.sh
RUN chmod +x /entry.sh

ENTRYPOINT ["/entry.sh"]
