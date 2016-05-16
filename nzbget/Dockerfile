FROM container4armhf/armhf-alpine:3.3

ENV NZBGET_VERSION 16.4
ENV NZB_TO_MEDIA_VERSION master

RUN apk add --no-cache ca-certificates python && \
    rm -rf /var/cache/apk/* && \
    mkdir /opt && cd /opt && \
    wget -O nzbget-linux.run https://github.com/nzbget/nzbget/releases/download/v$NZBGET_VERSION/nzbget-$NZBGET_VERSION-bin-linux.run && \
    /bin/sh /opt/nzbget-linux.run && \
    rm /opt/nzbget-linux.run && \
    wget -O nzbtomedia.tar.gz https://github.com/clinton-hall/nzbToMedia/archive/$NZB_TO_MEDIA_VERSION.tar.gz && \
    tar -xzvf nzbtomedia.tar.gz && \
    rm nzbtomedia.tar.gz && \
    mv /opt/nzbToMedia-$NZB_TO_MEDIA_VERSION/* /opt/nzbget/scripts && \
    rm -rf /opt/nzbToMedia-$NZB_TO_MEDIA_VERSION

EXPOSE 6789

CMD ["/opt/nzbget/nzbget", "-s", "-o", "outputmode=log"]
