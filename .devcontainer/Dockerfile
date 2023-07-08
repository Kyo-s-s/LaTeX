FROM archlinux:base-devel

ARG USER_ID=1000
RUN useradd -m -u ${USER_ID} docker

RUN pacman -Syyu --noconfirm \
    texlive-langjapanese \
    texlive-latexextra \
    texlive-binextra \
    perl-yaml-tiny \
    perl-file-homedir \
    ghostscript \
    git \
    curl \
    unzip \
    nodejs \
    npm

RUN git clone https://github.com/h-kitagawa/plistings.git \
    && mv /plistings/plistings.sty /usr/share/texmf-dist/tex/latex/listings/ \
    && mktexlsr

RUN curl -OL http://tug.ctan.org/tex-archive/macros/latex/contrib/algorithms.zip \ 
    && unzip algorithms.zip \
    && cd algorithms \
    && latex algorithms.ins \
    && cd .. \
    && mv algorithms /usr/share/texmf-dist/tex/latex/ \
    && mktexlsr

RUN curl -OL http://tug.ctan.org/tex-archive/macros/latex/contrib/algorithmicx.zip \
    && unzip algorithmicx.zip \
    && mv algorithmicx /usr/share/texmf-dist/tex/latex/ \
    && mktexlsr

RUN curl -OL https://ftp.kddilabs.jp/CTAN/macros/latex/contrib/thmbox.zip \
    && unzip thmbox.zip \
    && cd thmbox \
    && latex thmbox.ins \
    && latex thmbox.dtx \
    && cd .. \
    && mv thmbox /usr/share/texmf-dist/tex/latex/ \
    && mktexlsr
 

WORKDIR /home/docker