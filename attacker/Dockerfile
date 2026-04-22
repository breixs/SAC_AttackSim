FROM kalilinux/kali-rolling

RUN apt-get update && apt-get install -y \
    nmap \
    hydra \
    metasploit-framework \
    iputils-ping \
    netcat-traditional \
    ssh \
    wordlists

RUN gzip -d /usr/share/wordlists/rockyou.txt.gz

CMD ["tail", "-f", "/dev/null"]FROM kalilinux/kali-rolling
RUN apt-get update && apt-get install -y \
    nmap \
    hydra \
    metasploit-framework \
    iputils-ping \
    netcat-traditional \
    ssh
CMD ["tail", "-f", "/dev/null"]
