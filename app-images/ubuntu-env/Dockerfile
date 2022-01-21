FROM ubuntu:latest

RUN apt update \
    && apt install -y wine-binfmt \
    && update-binfmts --import /usr/share/binfmts/wine \
    && apt install -y git \
    && apt install -y gnutls-bin \
    && git config --global http.sslVerify false \
    && git config --global http.postBuffer 1048576000 \
    && git clone https://github.com/JanU-YieG/wechat_web_devtools.git \
    && cd wechat_web_devtools \
    && mkdir /root/.fonts \
    && mv ./Consolas.ttf /root/.fonts/ \
    && fc-cache -f \
    && ./bin/wxdt install \
    # && ./bin/update_package_nw.sh -l https://servicewechat.com/wxa-dev-logic/download_redirect?type=x64&from=mpwiki&download_version=1052111300&version_type=1 -v 1.05.2111300 \
    && ln -s $PWD/bin/wxdt /usr/bin/wxdt \
    && rm -rf /var/lib/apt/lists/* \
CMD ["/usr/bin/wxdt"]
