# TP1docker

5a. docker pull nginx

5b. docker images

5c. touch index.html

5d. docker run --name "TP1" -p 80:80 -v /Users/valentinhoudu/gitRepositories/TP1docker/:/usr/share/nginx/html nginx

5e. docker run -p 80:80 nginx 
    docker cp index.html TP1:/usr/share/nginx/html