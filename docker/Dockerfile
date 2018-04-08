FROM ubuntu:14.04

ADD prerequisites.sh /tmp
RUN DEBIAN_FRONTEND=noninteractive /tmp/prerequisites.sh 

#column command used by weOS but not installed by prerequisites.sh
#RUN apt-get install -y bsdmainutils cmake

RUN useradd -u 1000 -s /bin/bash -d /home/builder -m builder
RUN echo "builder ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

USER builder

RUN git config --global user.email 'kim.jaehwang@gmail'com'
RUN git config --global user.name 'Jaehwang Kim'

CMD ["/bin/bash"]
