FROM ubuntu:16.04

# To make it easier for build and release pipelines to run apt-get,
# configure apt to not require confirmation (assume the -y argument by default)
ENV DEBIAN_FRONTEND=noninteractive
RUN echo "APT::Get::Assume-Yes \"true\";" > /etc/apt/apt.conf.d/90assumeyes

RUN apt-get update \
&& apt-get install -y --no-install-recommends \
        ca-certificates \
        curl \
        jq \
        git \
        iputils-ping \
        libcurl3 \
        libicu55 \
        libunwind8 \
        netcat

RUN curl -O https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb && sudo dpkg -i packages-microsoft-prod.deb

RUN apt-get update \
&& apt-get install -y --no-install-recommends \
        apt-transport-https \
        dotnet-sdk-3.0

WORKDIR /azp

COPY ./start.sh .
RUN chmod +x start.sh

CMD ["./start.sh"]