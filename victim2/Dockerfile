FROM ubuntu:latest
RUN apt-get update && apt-get install -y openssh-server
RUN mkdir /var/run/sshd
RUN useradd -m -s /bin/bash admin_intern && echo 'admin_intern:SecretPass1990' | chpasswd
#flag
RUN echo "<Confidential data> Please do not steal!" > /home/admin_intern/confidential_info.txt
CMD ["/usr/sbin/sshd", "-D"]
