FROM container4armhf/armhf-alpine

ENV SICKRAGE_VERSION 4.2.5

RUN apk update && \
    apk add python python-dev py-pip py-libxml2 py-lxml ca-certificates \
            make gcc g++ openssl-dev libffi-dev unrar && \
    rm -rf /var/cache/apk/*

RUN pip --no-cache-dir install pyopenssl cheetah

RUN mkdir /opt && \
    cd /opt && \
    wget https://github.com/SiCKRAGETV/SickRage/archive/$SICKRAGE_VERSION.tar.gz && \
    tar -xzvf $SICKRAGE_VERSION.tar.gz && \
    rm $SICKRAGE_VERSION.tar.gz && \
    mv SickRage-$SICKRAGE_VERSION sickrage

EXPOSE 8081

CMD ["/usr/bin/python", "/opt/sickrage/SickBeard.py", "--nolaunch"]
