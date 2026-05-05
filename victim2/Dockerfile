FROM ubuntu:22.04
RUN apt-get update && apt-get install -y openssh-server
RUN mkdir -p /var/run/sshd
RUN useradd -m -s /bin/bash admin_intern && echo 'admin_intern:SecretPass1990' | chpasswd
#flag
RUN echo "<flag1> Confidential data!! Please do not steal!!\nBACKEND=http://192.168.10.40:80\nSTATUS=No_Autehtication\nNOTE=Access only from internal network!" > /home/admin_intern/confidential_info.txt
CMD ["/usr/sbin/sshd", "-D"]
