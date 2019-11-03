FROM node:12.11.1

RUN apt-get update
RUN apt-get install sudo

# Add atom
RUN apt-get install -y apt-transport-https ca-certificates
RUN wget -qO - http://packagecloud.io/AtomEditor/atom/gpgkey | apt-key add -
RUN sh -c 'echo "deb [arch=amd64] http://packagecloud.io/AtomEditor/atom/any/ any main" >> /etc/apt/sources.list'
RUN apt-get update
RUN apt-get install -y atom

RUN npm install -g typescript tslint ts-node

RUN sudo -u node apm install atom-typescript
RUN sudo -u node apm install atom-ide-ui linter linter-ui-default hyperclick intentions jumpy last-cursor-position find-selection Docblockr

RUN sudo -u node apm install busy-signal
RUN apt install -y emacs25
