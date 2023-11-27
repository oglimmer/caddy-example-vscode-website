FROM debian:latest

RUN apt-get update && apt-get install -y wget gpg apt-transport-https git && \
    wget -qO- https://packages.microsoft.com/keys/microsoft.asc | /usr/bin/gpg --dearmor > packages.microsoft.gpg && \
    install -D -o root -g root -m 644 packages.microsoft.gpg /etc/apt/keyrings/packages.microsoft.gpg && \
    sh -c 'echo "deb [arch=amd64,arm64,armhf signed-by=/etc/apt/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" > /etc/apt/sources.list.d/vscode.list' && \
    rm -f packages.microsoft.gpg

RUN apt-get update && \
    apt-get install -y code

RUN useradd vscode && mkdir -p /home/vscode/ && \
    chown -R vscode:vscode /home/vscode/

USER vscode

ENTRYPOINT [ "code" ]

CMD [ "tunnel" ]
