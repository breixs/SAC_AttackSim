FROM ubuntu:latest
RUN apt-get update && apt-get install -y openssh-server iputils-ping
RUN mkdir /var/run/sshd
# user cu parola slaba
RUN useradd -m -s /bin/bash user1 && echo 'user1:alexander' | chpasswd
# indiciu pentru parola Victimei 2
RUN mkdir -p /home/user1/network_endpoints/
RUN echo "IP = 192.168.10.30\nUSER = admin_intern\n" > /home/user1/network_endpoints/server_central.txt

# --- PARTEA NOUĂ: Structura complexă de fișiere ---
# Creăm un director "ascuns" de configurare sistemf

RUN chmod u+s /usr/bin/find

CMD ["/usr/sbin/sshd", "-D"]
