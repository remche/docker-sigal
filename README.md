# docker-sigal

Docker image based on nginx official one for [sigal](http://sigal.saimon.org/en/latest/) gallery.

Run with :
    docker run -p 80:80 -v /path/to/your/pictures/:/pictures --name sigal -d remche/sigal

default configuration :
- put gallery in /usr/share/nginx/html. You can use a docker volume if you want it permanent :
    docker run -p 80:80 -v /path/to/your/pictures/:/pictures -v sigal-html:/usr/share/nginx/html --name sigal -d remche/sigal
- use the galleria theme ;
- keep original, and symlink to ;

If you want to override this, you can use your own sigal.conf.py :
    docker run -p 80:80 -v /path/to/your/pictures/:/pictures -v/path/to/your/sigal.conf.py:/opt/sigal.conf.py --name sigal -d remche/sigal

You can set a basic authentication in htpasswd format setting HTPASSWD env variable :
    docker run -p 80:80 -v /path/to/your/pictures/:/pictures -e HTPASSWD='foo:$apr1$odHl5EJN$KbxMfo86Qdve2FH4owePn.' --name sigal -d remche/sigal
You might then use SSL with [nginx-proxy](https://hub.docker.com/r/jwilder/nginx-proxy/).


