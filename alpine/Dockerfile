# Pull base image.
FROM alpine

# for china
COPY repositories /etc/apk/repositories 

# add kaf client
ADD kaf /usr/bin
ADD config /root/.kaf/config

RUN apk update && apk add openssh-server jq mtr curl httpie bind-tools bind-tools tcpdump rsync util-linux pssh whois tcpflow socat openssl iptraf-ng iftop nload iperf ipcalc openssh-client --no-cache && \
    rm -rf /var/cache/apk/* /tmp/* && \
    ssh-keygen -A && passwd -d root 
ADD yimeng.keys /root/.ssh/authorized_keys
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]

