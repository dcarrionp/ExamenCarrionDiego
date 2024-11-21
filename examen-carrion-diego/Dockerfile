
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

COPY . /app

RUN npm install

RUN ng build --configuration production

RUN cp -r /app/dist/examen-carrion-diego/browser/* /var/www/html/

EXPOSE 80

CMD ["apachectl", "-D", "FOREGROUND"]