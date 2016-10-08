# docker-sigal

Docker image based on nginx official one for [sigal](http://sigal.saimon.org/en/latest/) gallery.

Run with :

    docker run -p 80:80 -v /path/to/your/pictures/:/pictures --name sigal-ct -d remche/docker-sigal


Default configuration use the galleria theme, keep original and put gallery in /usr/share/nginx/html. You can use a docker volume if you want it permanent :

    docker run -p 80:80 -v /path/to/your/pictures/:/pictures -v sigal-html:/usr/share/nginx/html --name sigal-ct -d remche/docker-sigal

    
If you want to override this conf, you can use your own sigal.conf.py :

    docker run -p 80:80 -v /path/to/your/pictures/:/pictures -v/path/to/your/sigal.conf.py:/opt/sigal.conf.py --name sigal-ct -d remche/docker-sigal


You can set a basic authentication in htpasswd format by setting HTPASSWD env variable :

    docker run -p 80:80 -v /path/to/your/pictures/:/pictures -e HTPASSWD='foo:$apr1$odHl5EJN$KbxMfo86Qdve2FH4owePn.' --name sigal-ct -d remche/docker-sigal


You might then use SSL with [nginx-proxy](https://hub.docker.com/r/jwilder/nginx-proxy/).


You can use the following command to regenerate gallery :

    docker exec sigal-ct sigal build


Using a cron or incron to run it is a good way to keep your gallery up to date.
