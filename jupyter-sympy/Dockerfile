FROM ubuntu:latest
RUN apt-get update
RUN apt install -y wget sudo python3.10 python3-pip libffi-dev

# for lcapy drawing (disabled because it's huge)
# ENV DEBIAN_FRONTEND=noninteractive
# RUN apt install -y texlive-latex-base texlive-fonts-recommended texlive-fonts-extra texlive-latex-extra

RUN python3.10 -m pip install jupyter jupyterlab sympy matplotlib
RUN python3.10 -m pip install lcapy

# Create user
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    chown ${uid}:${gid} -R /home/developer
RUN echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer

USER developer
CMD jupyter lab --ip 0.0.0.0 

WORKDIR /root