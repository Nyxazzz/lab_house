NextCloud
--------------------
🇬🇧 English Description  

Nextcloud is a self-hosted, open-source platform for file sharing, collaboration, and cloud services.  
It provides secure access to your data from any device and includes features such as calendar, contacts, video calls, and more.  
This repository contains a custom deployment of Nextcloud using Docker, optimized for personal or small business use.  

🇪🇸 Descripción en Español  

Nextcloud es una plataforma de código abierto y autohospedada para compartir archivos, colaborar y ofrecer servicios en la nube.  
Permite acceder de forma segura a tus datos desde cualquier dispositivo e incluye funciones como calendario, contactos, videollamadas, entre otras.  
Este repositorio contiene un despliegue personalizado de Nextcloud usando Docker, optimizado para uso personal o de pequeñas empresas.  

```bash
version: '3'

services:
  db:
    image: mariadb:10.5
    restart: always
    container_name: nextcloud-db
    volumes:
      - /srv/nextcloud/db:/var/lib/mysql
    environment:
      - MYSQL_ROOT_PASSWORD=rootpassword
      - MYSQL_PASSWORD=nextcloudpass
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud

  app:
    image: nextcloud
    restart: always
    container_name: nextcloud
    ports:
      - 8080:80
    volumes:
      - /srv/nextcloud/data:/var/www/html
    depends_on:
      - db
    environment:
      - MYSQL_PASSWORD=nextcloudpass
      - MYSQL_DATABASE=nextcloud
      - MYSQL_USER=nextcloud
      - MYSQL_HOST=db
```

