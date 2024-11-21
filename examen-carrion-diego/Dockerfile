#Creación de Dockerfile:

    #Desarrolla un Dockerfile que parta de la imagen base de Debian.
    #Instala Apache como servidor web.
    #Instala Node.js y npm para gestionar y ejecutar la aplicación Angular.
    #Utiliza npm para instalar Angular CLI globalmente dentro de la imagen.

FROM debian:latest

RUN apt-get update && apt-get install -y \
    apache2 \
    curl \
    gnupg \
    build-essential


RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - && \
    apt-get install -y nodejs


RUN node -v && npm -v

RUN npm install -g @angular/cli

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN ng build --configuration production

RUN rm -rf /var/www/html/* && \
    cp -r /app/dist/angular-docker-app/browser/* /var/www/html/

EXPOSE 80

CMD ["apachectl", "-D", "FOREGROUND"]
