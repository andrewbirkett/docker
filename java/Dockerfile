FROM ubuntu:latest

RUN apt-get update
RUN apt install -y wget sudo
RUN apt install -y openjdk-11-jdk openjdk-8-jdk gradle maven

# Create user
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    chown ${uid}:${gid} -R /home/developer
RUN echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer

# Intellij
RUN wget https://download.jetbrains.com/idea/ideaIC-2019.2.3.tar.gz
RUN (cd /home/developer; tar zxvf /ideaIC-2019.2.3.tar.gz)

# Default to java8; ubuntu comes with old gradle that doesn't grok java11
RUN echo 2 | update-alternatives --config java # 

USER developer
ENV HOME /home/developer






