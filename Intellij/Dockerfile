# $ export DISPLAY=192.168.100.13:0.0
# $ docker build . -t [image-name]
# $ XSOCK=/tmp/.X11-unix && sudo docker run -i -v $XSOCK:$XSOCK -e DISPLAY -u developer -t [image-name]
# Then run IntelliJ with:
# /ideaIU-2019.3.3/bin/idea.sh
# http://luozengbin.github.io/blog/2014-06-21-%5B%E3%83%A1%E3%83%A2%5D%E3%83%AA%E3%83%A2%E3%83%BC%E3%83%88x%E3%81%AE%E6%8E%A5%E7%B6%9A%E6%96%B9%E6%B3%95.html
FROM alpine:3.8
ENV LANG C.UTF-8
RUN set -ex && \
    apk add --no-cache --update \
    # basic packages
        bash bash-completion coreutils file grep openssl openssh nano sudo tar xz \
    # debug tools
        gdb musl-dbg strace \
    # docs and man
        bash-doc man man-pages less less-doc \
    # GUI fonts
        font-noto \
    # user utils
        shadow
RUN set -ex && \
    apk add --no-cache --update \
    # C++ build tools
        cmake g++ git linux-headers libpthread-stubs make
RUN set -ex && \
    apk add --no-cache --update \
    # Java tools
        gradle openjdk8 openjdk8-dbg
# Install IntelliJ Community
RUN set -ex && \
    wget https://download-cf.jetbrains.com/idea/ideaIU-2019.3.3.tar.gz && \
    tar -xf ideaIU-2019.3.3.tar.gz && \
    rm ideaIU-2019.3.3.tar.gz
# Create a new user with no password
ENV USERNAME developer
RUN set -ex && \
    useradd --create-home --key MAIL_DIR=/dev/null --shell /bin/bash $USERNAME && \
    passwd -d $USERNAME
# Set additional environment variables
ENV JAVA_HOME /usr/lib/jvm/java-1.8-openjdk
ENV JDK_HOME  /usr/lib/jvm/java-1.8-openjdk
ENV JAVA_EXE  /usr/lib/jvm/java-1.8-openjdk/bin/java
