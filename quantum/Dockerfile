FROM ubuntu:latest
RUN sed --in-place --regexp-extended "s/(\/\/)(archive\.ubuntu)/\1uk.\2/" /etc/apt/sources.list && apt-get update && apt-get upgrade --yes
RUN apt install -y python3
RUN apt install -y python3-pip


RUN pip3 install qiskit
RUN pip3 install qiskit-terra[visualization]

RUN apt install -y curl net-tools
RUN apt install -y sudo

# Create user
RUN export uid=1000 gid=1000 && \
    mkdir -p /home/developer && \
    echo "developer:x:${uid}:${gid}:Developer,,,:/home/developer:/bin/bash" >> /etc/passwd && \
    echo "developer:x:${uid}:" >> /etc/group && \
    chown ${uid}:${gid} -R /home/developer
RUN echo "developer ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/developer && \
    chmod 0440 /etc/sudoers.d/developer

USER developer
CMD jupyter notebook --ip 172.17.0.2 --port 8989


