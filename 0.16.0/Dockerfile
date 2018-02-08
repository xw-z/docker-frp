FROM ubuntu:16.04

LABEL AUTHOR="xwzhou@yeah.net"

ENV FRP_VERSION=0.16.0

RUN apt update \
&& apt install -y wget

WORKDIR /tmp
RUN set -x \
&& wget https://github.com/fatedier/frp/releases/download/v${FRP_VERSION}/frp_${FRP_VERSION}_linux_amd64.tar.gz \
&& tar -zxf frp_${FRP_VERSION}_linux_amd64.tar.gz \
&& mv frp_${FRP_VERSION}_linux_amd64 /frp \
&& mkdir -p /frp \
&& apt remove -y wget \
&& apt autoremove -y \
&& rm -rf /var/lib/apt/lists/*

COPY conf/frps.ini /frp/conf/frps.ini

VOLUME /frp/conf

WORKDIR /frp
ENTRYPOINT /frp/frps -c /frp/conf/frps.ini