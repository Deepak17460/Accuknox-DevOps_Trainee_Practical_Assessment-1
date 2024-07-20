FROM ubuntu:22.04

RUN apt-get update && \
    apt-get install -y \
    netcat \
    fortune-mod \
    cowsay \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

#Add /usr/games to PATH
ENV PATH="/usr/games:${PATH}"

WORKDIR /usr/src/app

COPY wisecow.sh .

RUN chmod +x wisecow.sh

EXPOSE 4499

CMD ["./wisecow.sh"]
