FROM kalilinux/kali-last-release

RUN apt-get update && apt-get install -y \
    nmap \
    hydra \
    metasploit-framework \
    iputils-ping \
    netcat-traditional \
    ssh \
    wordlists \
    proxychains4 \
    curl

RUN gzip -d /usr/share/wordlists/rockyou.txt.gz || true

CMD ["tail", "-f", "/dev/null"]
