# TP1docker

Répertoire courant : /Users/valentinhoudu/gitRepositories/TP1docker

5a. 'docker pull nginx'

5b. 'docker images'

5c. 'touch index.html'

5d. 'docker run --name "TP1" -p 80:80 -v /Users/valentinhoudu/gitRepositories/TP1docker/:/usr/share/nginx/html nginx'

5e. 'docker run -p 80:80 nginx 
    docker cp index.html TP1:/usr/share/nginx/html'

6a. J'ai créé un Dockerfile dans le répertoire courant 
    'docker build -t tp1 .'

6b. 'docker run --name "TP1" -p 80:80 -d tp1'

6c. La seconde question fait que l'on renseigne directement l'image et le volume dans dockerfile. La première quetion on ne renseigne que le port et le volume avec docker run. Pareil pour l'image.

7a. 'docker pull phpmyadmin/phpmyadmin'
    'docker pull mysql'

7b. 'docker run --name mysql -e MYSQL_ROOT_PASSWORD=123 -d mysql' 
    'docker run --name phpmyadmin -d --mysql:db -p 8081:80 phpmyadmin/phpmyadmin'
    se connecter sur http://localhost:8081

    Connection avec root et mot de passe : 123
    ```
    CREATE DATABASE test;
    use test_creation;
    CREATE TABLE table_name (
        column1 INT,
        column2 INT
    );
    ```

8a. creation du fichier docker-compose.up
    'docker compose up' (dans répertoire courant)
    se connecter sur http://localhost:8081
    Connection avec root et mot de passe : 123

    -> Il permet de configurer les serveurs de façon rapide, et surtout d'avoir le code en dur sur un seul et même fichier. Par besoins de préparer plusieurs commandes, toute la configuration se fait d'un seul tenant

8b. volumes:
      - ./initdb:/var/lib/mysql
      - ./initdb.sql:/docker-entrypoint-initdb.d/0_init.sql
    environment:
      MYSQL_DATABASE: test-db
      MYSQL_USER: admin
      MYSQL_PASSWORD: 123
      MYSQL_ROOT_PASSWORD: 123
    
    Dans le fichier docker-compose.yml il est possible de spécifier les volumes, et nottament un fichier initdb.sql qui permet de creer des tables et ajouter des données lors de la constrution du container. 
    L'environnement permet de definir un utilisateur 

9a. /question9/docker-compose.yml

    bash-5.1# ping web
    ping: web: Name does not resolve
    bash-5.1# ping app
    PING app (172.30.0.3) 56(84) bytes of data.
    64 bytes from app.backend (172.30.0.3): icmp_seq=1 ttl=64 time=0.070 ms

9b.Il y a plusisuers lignes, tout d'abord il   n'y a pas les mêmes réseaux. Impossivle pour les machines de se ping l'une et l'autre.
Ensuite, l'id network n'est pas indiqu" pour db et web. 

9c. 