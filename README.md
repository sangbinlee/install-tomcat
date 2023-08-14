# install-tomcat
install-tomcat



# file docker-compose.yml

# docker-compose up -d
# docker-compose down



# docker-compose start web

# docker-compose stop web



# docker-compose ps
# docker-compose logs -f web

# vi setenv.sh
    root@kpismain:~# vi setenv.sh
      #!/bin/sh
      
      export JAVA_OPTS="${JAVA_OPTS} -Dsystem.mode=dev"
      export JAVA_OPTS="${JAVA_OPTS} -Dlog.location=/usr/local/tomcat/logs/part-zone"
      # UMASK="0022"

# docker cp ~/setenv.sh tomcat-test:/usr/local/tomcat/bin/
    
    
    root@kpismain:~#  docker cp ~/setenv.sh tomcat-test:/usr/local/tomcat/bin/
    Successfully copied 2.05kB to tomcat-test:/usr/local/tomcat/bin/
    root@kpismain:~# vi setenv.sh
    root@kpismain:~# vi setenv.sh
    root@kpismain:~# docker cp ~/setenv.sh tomcat-test:/usr/local/tomcat/bin/
    Successfully copied 2.05kB to tomcat-test:/usr/local/tomcat/bin/




