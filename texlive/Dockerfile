FROM archlinux/archlinux:base-devel

# WORKAROUND for glibc 2.33 and old Docker
# See https://github.com/actions/virtual-environments/issues/2658
RUN patched_glibc=glibc-linux4-2.33-4-x86_64.pkg.tar.zst && \
    curl -LO "https://repo.archlinuxcn.org/x86_64/$patched_glibc" && \
    bsdtar -C / -xvf "$patched_glibc"

RUN pacman -Syu --needed --noconfirm texlive-most ttf-ubuntu-font-family; pacman -Scc --noconfirm

WORKDIR /root
RUN mkdir -p /usr/local/share/fonts/ttf
RUN curl -L https://github.com/FortAwesome/Font-Awesome/archive/v4.7.0.tar.gz -o fontawesome.tar.gz && \
    tar -xzf fontawesome.tar.gz && \
    cp Font-Awesome*/fonts/*ttf /usr/local/share/fonts/ttf/ && \
    rm -rf Font-Awesome* fontawesome.tar.gz

RUN ln -s /etc/fonts/conf.avail/09-texlive-fonts.conf /etc/fonts/conf.d/09-texlive-fonts.conf && \
    fc-cache

WORKDIR /mnt
