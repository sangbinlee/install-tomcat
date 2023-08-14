# install-tomcat
install-tomcat



# file docker-compose.yml

    
    
    version: '3.4'
    
    services:
      tomcat:
        container_name: "tomcat-test"
        image: tomcat:8
        environment: # 환경 변수 값
          - system.mode=dev
          - log.location=/usr/local/tomcat/logs/part-zone
        volumes: # 볼륨 마운트
          - /root/ROOT.war:/usr/local/tomcat/webapps/ROOT.war
        ports:
          - "8080:8080"
    
    






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




