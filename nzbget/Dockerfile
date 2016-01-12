FROM container4armhf/armhf-alpine

ENV NZBGET_VERSION 16.4

RUN apk update && apk add ca-certificates && \
    mkdir /opt && cd /opt && \
    wget -O nzbget-linux.run https://github.com/nzbget/nzbget/releases/download/v$NZBGET_VERSION/nzbget-$NZBGET_VERSION-bin-linux.run && \
    /bin/sh /opt/nzbget-linux.run && \
    rm /opt/nzbget-linux.run 

EXPOSE 6789

CMD ["/opt/nzbget/nzbget", "-s", "-o", "outputmode=log"]
