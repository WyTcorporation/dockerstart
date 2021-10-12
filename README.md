https://totaku.ru/ustanovka-lemp-s-pomoshchiu-dockera/
https://webdevkin.ru/posts/raznoe/docker

//Проверяем стоит ли докер
docker -v && docker-compose -v

//windows
https://docs.microsoft.com/ru-ru/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package

//Создание нужных папок
mkdir www www/hello.test mysql logs hosts images images/php && echo "<?php phpinfo();" > www/hello.test/index.php && touch images/php/php.ini && touch images/php/Dockerfile && touch docker-compose.yml

//host
127.0.0.1 hello.test
//url
http://hello.test:8000/

//mysql
http://localhost:8183/

      MYSQL_USERNAME: root
      MYSQL_ROOT_PASSWORD: secret

//mongo
http://localhost:8081/
MONGO_INITDB_ROOT_USERNAME: root
MONGO_INITDB_ROOT_PASSWORD: example

//mongo
http://localhost:8081/
MONGO_INITDB_ROOT_USERNAME: root
MONGO_INITDB_ROOT_PASSWORD: example

//Устанавливаем
docker-compose up

docker-compose up --build

//это
docker-compose up --build -d

//сносим все
docker-compose down

docker-compose logs -f
