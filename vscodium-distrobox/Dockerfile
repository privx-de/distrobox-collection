# Use Fedora Toolbox Image
FROM registry.fedoraproject.org/fedora-toolbox:latest

# Configure RPM Fusion
RUN dnf -y install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm \
    https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm

# Install Intel Media Driver
RUN dnf -y install intel-media-driver libva-utils

# Link to host dbus
RUN mkdir /run/dbus && ln -s /run/host/run/dbus/system_bus_socket /run/dbus/system_bus_socket

# Install VSCodium
COPY vscodium.repo /etc/yum.repos.d/vscodium.repo
RUN rpmkeys --import https://gitlab.com/paulcarroty/vscodium-deb-rpm-repo/-/raw/master/pub.gpg
RUN dnf -y install codium

# Install extra tools
RUN dnf -y install shellcheck

# Entry
CMD /bin/bash
