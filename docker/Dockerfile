FROM ubuntu:18.04

RUN \
    apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y \
        unzip \
        wget \
        postgresql \
        postgresql-contrib \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -ms /bin/bash zoho

ADD ./responses.txt /home/zoho

RUN cd /home/zoho && wget https://www.zoho.com/analytics/65482/Zoho_Analytics_64bit.bin

RUN chmod 755 /home/zoho/Zoho_Analytics_64bit.bin
RUN ls -la /home/zoho
RUN mkdir /app && chown zoho /app

USER zoho

# Silent mode does not work with free version.
# Feel free to change flag "-i" to silent and try to install it.
RUN cat /home/zoho/responses.txt | /home/zoho/Zoho_Analytics_64bit.bin -i console
RUN chmod +x /app/Analytics/bin/StartServer.sh
RUN rm /home/zoho/Zoho_Analytics_64bit.bin

WORKDIR /app/Analytics/bin

CMD ["/bin/bash", "./StartServer.sh"]
