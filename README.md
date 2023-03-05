# TP1docker

Répertoire courant : /Users/valentinhoudu/gitRepositories/TP1docker

5a. docker pull nginx

5b. docker images

5c. touch index.html

5d. docker run --name "TP1" -p 80:80 -v /Users/valentinhoudu/gitRepositories/TP1docker/:/usr/share/nginx/html nginx

5e. docker run -p 80:80 nginx 
    docker cp index.html TP1:/usr/share/nginx/html

6a. J'ai créé un Dockerfile dans le répertoire courant 
    docker build -t tp1 . 

6b. docker run --name "TP1" -p 80:80 -d tp1

6c. La première méthode fait que le volume est synchronisé au répertoire sur le PC. Un changelent sur 'lun ou l'autre impacte forcement les deux coters. La seconde méthode permet de ne pas avoir de synchronisation