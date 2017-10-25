Default site 80 Port (with elegant link, Nginx cache settings) + Composer function and can run PHP Framework Laravel5

    You can modify the corresponding data for nginx and host settings

    Can be used with Kitematic (DockerHub Link)

    The current image is about 1.144 GB

How To Setting

Modify the site root (restart the container after modification)

$ vi home / config / virtualhost / sample.conf

Modify NGINX settings (restart the container after modification is complete)

$ vi home / config / nginx / nginx.conf

Modify the PHP.INI settings (restart the container after the modification is complete)

$ vi home / config / php.ini

Modify the Crontab settings (restart the container after the completion of the change, pay attention to the format can not be wrong, if the error can be seen in the start message)

$ vi home / config / Crontab

Modify the Supervisor settings (restart the container after the completion of the change, pay attention to the format can not be wrong, if the error can be seen in the start message)

$ vi home / config / supervisord.conf

    Added process management

Create the home / wwwconfig / supervisord / * conf file


You can refer to home / wwwconfig / supervisord.conf the bottom of the sample (please note that you need to set up empty log files)

$ supervisorctl start laravel-worker: *

Backup SSH KEY, Nginx, PHP.ini, Hosting Config

$ sh ~ / backup-to-hosting.sh

Re-read and restart Nginx (the command will overwrite the home / config profile to the current profile)

$ sh ~ / nginx-reload.sh

Working Directory

    home / config / set the relevant file (if necessary, please restart the container)

    home / log / event record related files

    home / root / site related files

Link Mariadb-Docker (official version) optional

https://hub.docker.com/r/library/mariadb/

Setting Password in Environment Variables [MYSQL_ROOT_PASSWORD = {your password}]

or

$ docker run --name some-mariadb -e MYSQL_ROOT_PASSWORD = my-secret-pw -d mariadb: tag

use exec enter command change zone time in taiwan

$ cp -p / usr / share / zoneinfo / Asia / Taipei / etc / localtime

Use Mariadb-Docker (imagine10255) optional

[imagine10255 / centos6-mariadb] (https://hub.docker.com/r/imagine10255/centos6-mariadb)
Link Redis-Docker Optional

https://hub.docker.com/r/library/redis/

 How to run:

$ docker run -d -p 6379: 6379 --name redis redis

Link Mailcatcher-Docker Optional

https://hub.docker.com/r/schickling/mailcatcher/

$ docker run -d -p 1080: 1080 --name mailcatcher schickling / mailcatcher

Composer Package

Envoy 1.0.25 task execution

$ envoy

How To Use Tool

enter-container.sh Enter the container

$ sh enter-container.sh {CONTAINERID NAME}

create-container.sh Create container

$ sh create-container.sh

build-container.sh re-use DockerFile to create an image

$ sh build-container.sh

push-images.sh Use DockerHub to upload image files

$ sh push-images.sh

delete-images.sh Delete waste image file <none> name (associated container must have been deleted)

$ sh delete-images.sh

Catalog History

2015-12-12 Add SSH connection (password default P @ ssw0rd)

2015-12-13 Added Crontab Schedule Management

2015-12-13 Added TimeZone Asia / Taipei CST Time Zone

2015-12-19 new Supervisor process management

2015-12-19 upgrade git-1.7.1-> 2.6.3

2015-12-20 New SSH Key Reserved, Backup Config

2016-06-17 modify php.ini max_input_vars allows the transmission of 9999 input
extension = ssh2.so

$ yum install php56w-common
$ yum install libssh2 libssh2-devel make
$ yum install php56w-devel
$ pecl install ssh2-0.11.3
$ echo extension = ssh2.so> /etc/php.d/ssh2.ini

Confirmation and testing

$ php -m | grep ssh2

B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
B
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
A
$ php -r "ssh2_connect ();"
