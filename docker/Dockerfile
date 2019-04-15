FROM ubuntu:18.04

RUN \
    apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
        unzip \
        postgresql \
        postgresql-contrib \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -ms /bin/bash zoho

#ADD ./docker/Zoho_Analytics_64bit.bin /home/zoho
ADD ./docker/responses.txt /home/zoho
ADD https://www.zoho.com/analytics/65482/Zoho_Analytics_64bit.bin /home/zoho/Zoho_Analytics_64bit.bin

RUN chmod 755 /home/zoho/Zoho_Analytics_64bit.bin
RUN ls -la /home/zoho
RUN mkdir /src && chown zoho /src

USER zoho

# Silent mode does not work with free version.
# Feel free to change flag "-i" to silent and try to install it.
RUN cat /home/zoho/responses.txt | /home/zoho/Zoho_Analytics_64bit.bin -i console
RUN chmod +x /src/Analytics/bin/StartServer.sh
VOLUME ["/src"]
WORKDIR /src/Analytics/bin
