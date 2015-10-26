FROM ubuntu:14.04

ENV DEBIAN_FRONTEND noninteractive

RUN locale-gen en_US.UTF-8
RUN update-locale LANG=en_US.UTF-8

RUN apt-get update -y
RUN apt-get install -y openssh-server

RUN mkdir /var/run/sshd
RUN echo root:root | chpasswd
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
RUN sed -ri 's/#UsePAM no/UsePAM no/g' /etc/ssh/sshd_config
RUN sed -ri 's/PermitRootLogin without-password/PermitRootLogin yes/g' /etc/ssh/sshd_config

EXPOSE 22
CMD    ["/usr/sbin/sshd", "-D"]
