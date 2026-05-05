FROM ubuntu:22.04
# Instalam python3 si curl (pentru debug)
RUN apt-get update && apt-get install -y python3 curl

# Cream folderul pentru site
RUN mkdir -p /var/www/html
WORKDIR /var/www/html

# Pagina Confidentiala - tinta finala
RUN echo "<!DOCTYPE html><html><head><title>Flag 2</title></head><body><h1>SUPER SECRET DATA</h1><p>Only for employees on the 192.168.10.x network!</p></body></html>" > index.html

# Pornim serverul web pe portul 80
CMD ["python3", "-m", "http.server", "80"]
