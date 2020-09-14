# docker build -t ctf:ubuntu18.04
# docker run --rm -v $PWD:/cmount --cap-add=SYS_PTRACE --security-opt seccomp=unconfined -d --name ctf -i ctf:ubuntu18.04
# docker exec -it ctf /bin/bash

FROM ubuntu:18.04

ENV LC_CTYPE C.UTF-8
ENV DEBIAN_FRONTEND=noninteractive
RUN dpkg --add-architecture i386 && \
apt-get update && \
apt-get install -y build-essential jq strace ltrace curl wget rubygems gcc dnsutils netcat gcc-multilib net-tools vim gdb gdb-multiarch python python3 python3-pip python3-dev libssl-dev libffi-dev wget git make procps libpcre3-dev libdb-dev libxt-dev libxaw7-dev python-pip libc6:i386 libncurses5:i386 libstdc++6:i386 perl wget rpm2cpio cpio zstd
RUN pip install capstone requests pwntools r2pipe
RUN pip3 install pwntools keystone-engine unicorn capstone ropper
RUN mkdir tools && cd tools
RUN git clone https://github.com/JonathanSalwan/ROPgadget 
RUN git clone https://github.com/radare/radare2 && cd radare2 && sys/install.sh 
RUN cd .. && git clone https://github.com/pwndbg/pwndbg && cd pwndbg && git checkout stable && ./setup.sh
RUN cd .. && git clone https://github.com/niklasb/libc-database && cd libc-database && ./get all
RUN gem install one_gadget
