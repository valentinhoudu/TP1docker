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

6c. La première méthode fait que le volume est synchronisé au répertoire sur le PC. Un changelent sur 'lun ou l'autre impacte forcement les deux coters. La seconde méthode permet de ne pas avoir de synchronisation

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