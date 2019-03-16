FROM archlinux/base

RUN pacman -Sy --needed --noconfirm base-devel texlive-most ttf-ubuntu-font-family; pacman -Scc --noconfirm

WORKDIR /root
RUN curl -L https://github.com/FortAwesome/Font-Awesome/archive/v4.7.0.tar.gz -o fontawesome.tar.gz && \
    tar -xzf fontawesome.tar.gz && \
    cp Font-Awesome*/fonts/*ttf /usr/share/fonts/TTF/ && \
    rm -rf Font-Awesome* fontawesome.tar.gz

RUN ln -s /etc/fonts/conf.avail/09-texlive-fonts.conf /etc/fonts/conf.d/09-texlive-fonts.conf && \
    fc-cache && mkfontscale && mkfontdir

WORKDIR /mnt 


