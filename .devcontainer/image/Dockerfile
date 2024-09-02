FROM fedora:latest

RUN dnf upgrade -y
RUN dnf install -y \
  \"Fedora\ Server\ Edition\" \"Development\ and\ Creative\ Workstation\" \
  \"Administration\ Tools\" \"C\ Development\ Tools\ and\ Libraries\" \
  \"Cloud\ Infrastructure\" \"Cloud\ Management\ Tools\" \"Container\ Management\" \
  \"D\ Development\ Tools\ and\ Libraries\" \"Development\ Tools\" \"Editors\" \
  \"Headless\ Management\" \"Network\ Servers\" \"RPM\ Development\ Tools\" \
  \"Security\ Lab\" \"Text\-based\ Internet\" \"Hardware\ Support\" \"System\ Tools\"
RUN dnf install dotnet-sdk-8.0 aspnetcore-runtime-8.0 -y 
RUN dnf distro-sync -y
RUN dnf makecache -y
RUN dotnet tool install -g x ef

COPY files/entry.sh /entry.sh
RUN chmod +x /entry.sh

ENTRYPOINT ["/entry.sh"]
