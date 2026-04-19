FROM ubuntu:latest
RUN apt-get update && apt-get install -y openssh-server iputils-ping
RUN mkdir /var/run/sshd
# Cream un user cu parola slaba: user1 / password123
RUN useradd -m -s /bin/bash user1 && echo 'user1:password123' | chpasswd
# Adaugam un indiciu pentru Lateral Movement (parola Victimei 2)
RUN echo "Parola catre serverul intern (Victima 2) este: secret456" > /home/user1/note.txt
CMD ["/usr/sbin/sshd", "-D"]
