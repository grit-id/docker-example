FROM gcc:latest
COPY . /usr/src/myapp
WORKDIR /usr/src/myapp

RUN echo "deb http://download.opensuse.org/repositories/network:/messaging:/zeromq:/release-stable/Debian_9.0/ ./" >> /etc/apt/sources.list
RUN wget https://download.opensuse.org/repositories/network:/messaging:/zeromq:/release-stable/Debian_9.0/Release.key -O- | apt-key add
RUN apt-get update
RUN wget http://ftp.br.debian.org/debian/pool/main/libs/libsodium/libsodium18_1.0.11-2_amd64.deb
RUN dpkg -i libsodium18_1.0.11-2_amd64.deb
RUN yes | apt-get install libzmq5
RUN yes | apt-get install libzmq3-dev


RUN cc serverzmq.c -lzmq -o serverzmq
RUN cc clientzmq.c -lzmq -o clientzmq

CMD ["./serverzmq"]
CMD ["./clientzmq"]

LABEL Name=zmq_cs Version=1.0.0