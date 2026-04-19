FROM ubuntu:latest
RUN apt-get update && apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN useradd -m -s /bin/bash admin_intern && echo 'admin_intern:secret456' | chpasswd
# Fisierul "tezaur"
RUN echo "Felicitari! Ai ajuns la datele confidentiale." > /home/admin_intern/flag.txt
CMD ["/usr/sbin/sshd", "-D"]
