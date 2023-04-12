# P05---Despliegue-de-aplicaciones-web-con-docker-compose
P05 - Despliegue de aplicaciones web con docker compose
P05 - Despliegue de escenarios multicontenedor con Docker Compose

Las aplicaciones a desplegar son: 

- Servidor web Apache

Descargamos la imagen httpd:![](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/Servidor%20web%20Apache/Capturas/Pull%20imagen%20.png)

Para desplegar el contenedor ponemos docker compose up –d (-d es opcional, detached mode sirve para ejecutar contenedores en segundo plano):

![]([https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/fc187a8cc2fbe266449f7ad934d7cc82565eca69/Servidor%20web%20Apache/Capturas/Pull%20imagen%20.png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/Servidor%20web%20Apache/Capturas/docker%20compose%20up%20-d%20.png)



Para verlo en la web podemos dar clic derecho en la imagen desde el Visual Studio Code y darle a “Open in Browser” o en el buscador de internet poner localhost:8080:

![]([Servidor web Apache/Capturas/Open in browse .png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/Servidor%20web%20Apache/Capturas/Open%20in%20browse%20.png)

Datos del docker-compose.yml:

```
version: '3.1'

services:

`  `apache:

`    `image: httpd:latest

`    `container\_name: my-apache-app

`    `ports:

`    `- '8080:80'

`    `volumes:

`    `- ./website:/usr/local/apache2/htdocs

```



- Mediawiki 

Descargamos la imagen Mediawiki:![]([Aspose.Words.8861e317-3906-4af9-abe1-06f4572474aa.004.png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/Mediawiki/Capturas/Docker%20pull%20.png)

Para desplegar el contenedor ponemos docker compose up –d:

![]([Aspose.Words.8861e317-3906-4af9-abe1-06f4572474aa.005.png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/Mediawiki/Capturas/Docker%20compose%20up%20-d%20.png)

Lo vemos en la web:

![]([Aspose.Words.8861e317-3906-4af9-abe1-06f4572474aa.006.png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/Mediawiki/Capturas/Open%20in%20browser%20.png)

Datos del docker-compose.yml:

```

version: '3.2'

services:

`  `web:

`    `image: mediawiki

`    `ports:

`      `- 80:80

`    `volumes:

`      `#- ./LocalSettings.php:/var/www/html/LocalSettings.php

`      `- database:/var/www/data

`      `- images:/var/www/html/images

volumes:

`    `database:

`    `images:

```


- Guestbook 

Descargamos la imagen Guestbook:

![]([Aspose.Words.8861e317-3906-4af9-abe1-06f4572474aa.007.png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/Guestbook/Capturas/pull%20imagen.png)

Para desplegar el contenedor ponemos docker compose up –d:![]([Aspose.Words.8861e317-3906-4af9-abe1-06f4572474aa.008.png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/Guestbook/Capturas/docker%20compose%20up%20-d.png)

Datos del docker-compose.yml:


```
version: '3.1'

services:

`  `app:

`    `container\_name: guestbook-compose

`    `image: iesgn/guestbook

`    `restart: always

`    `ports:

`      `- 80:8080

`  `db:

`    `container\_name: redis-compose

`    `image: redis

`    `restart: always
```





- Wordpress 

Descargamos la imagen Wordpress	:

![]([Aspose.Words.8861e317-3906-4af9-abe1-06f4572474aa.009.png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/Wordpress/Capturas/imagen%20pull.png)

Para desplegar el contenedor ponemos docker compose up –d:

![]([Aspose.Words.8861e317-3906-4af9-abe1-06f4572474aa.010.png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/Wordpress/Capturas/Docker%20compose%20up%20-d.png)

Lo vemos en la web:![]([Aspose.Words.8861e317-3906-4af9-abe1-06f4572474aa.011.png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/Wordpress/Capturas/Open%20in%20browser.png)

Datos del docker-compose.yml:

```
version: '3.1'

services:

`  `wordpress:

`    `container\_name: servidor\_wp-compose

`    `image: wordpress

`    `restart: always

`    `environment:

`      `WORDPRESS\_DB\_HOST: db

`      `WORDPRESS\_DB\_USER: user\_wp

`      `WORDPRESS\_DB\_PASSWORD: asdasd

`      `WORDPRESS\_DB\_NAME: bd\_wp

`    `ports:

`      `- 80:80

`    `volumes:

`      `- wordpress\_data:/var/www/html/wp-content

`  `db:

`    `container\_name: servidor\_mysql-compose

`    `image: mariadb

`    `restart: always

`    `environment:

`      `MYSQL\_DATABASE: bd\_wp

`      `MYSQL\_USER: user\_wp

`      `MYSQL\_PASSWORD: asdasd

`      `MYSQL\_ROOT\_PASSWORD: asdasd

`    `volumes:

`      `- mariadb\_data:/var/lib/mysql

volumes:

`    `wordpress\_data:

`    `mariadb\_data:
```





- adminer 

Descargamos la imagen adminer:

![]([Aspose.Words.8861e317-3906-4af9-abe1-06f4572474aa.012.png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/adminer/Capturas/pull%20imagen.png)


Para desplegar el contenedor ponemos docker compose up –d:

![]([Aspose.Words.8861e317-3906-4af9-abe1-06f4572474aa.013.png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/adminer/Capturas/docker%20compose%20up%20-d%20.png)

Lo vemos en la web:

![]([Aspose.Words.8861e317-3906-4af9-abe1-06f4572474aa.014.png](https://github.com/JaimePastor6/P05---Despliegue-de-aplicaciones-web-con-docker-compose/blob/b0be91ecf9e3ac53b31ce218535423868d7b2562/adminer/Capturas/open%20in%20browser.png)



Datos del docker-compose.yml:

```
version: '3.1'

services:

`  `adminer:

`    `image: adminer

`    `restart: always

`    `ports:

`      `- 8080:8080

`  `db:

`    `image: mysql:5.6

`    `restart: always

`    `environment:

`      `MYSQL\_ROOT\_PASSWORD: example

```












Jaime Pastor
