FROM ubuntu:14.04

MAINTAINER Jaehwang Kim <kim.jaehwang@gmail.com>

ARG UID=1000

ADD prerequisites.sh /tmp
RUN DEBIAN_FRONTEND=noninteractive /tmp/prerequisites.sh 
RUN rm /tmp/prerequisites.sh 

RUN useradd -u $UID -s /bin/bash -d /home/builder -m builder
RUN echo "builder ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER builder

RUN git config --global user.email 'kim.jaehwang@gmail.com'
RUN git config --global user.name 'Jaehwang Kim'

CMD ["/bin/bash"]
