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



# chmod +x setenv.sh
# chmod 755 setenv.sh
    
    root@kpismain:~# chmod 755 setenv.sh
    root@kpismain:~# ll
    total 125164
    drwx------ 16 root   root        4096 Aug 14 04:20 ./
    drwxr-xr-x 19 root   root        4096 Aug  5 00:39 ../
    -rw-------  1 root   root        8891 Aug 13 15:25 .bash_history
    -rw-r--r--  1 root   root        3106 Oct 15  2021 .bashrc
    drwxr-xr-x  3 root   root        4096 Aug  5 07:28 .cache/
    drwxr-xr-x  3 root   root        4096 Aug  5 07:27 .config/
    drwx------  3 root   root        4096 Aug 10 23:04 .docker/
    -rw-r--r--  1 root   root         211 Aug  5 04:47 docker-compose-httpd.yml
    -rw-r--r--  1 root   root         524 Aug  5 04:48 docker-compose-tomcat.yml
    -rw-r--r--  1 root   root         326 Aug 13 15:11 docker-compose.yml
    drwxr-xr-x  6 root   root        4096 Aug  5 15:42 Docker-Httpd-Tomcat/
    drwxr-xr-x  8 root   root        4096 Aug  5 06:14 docker-httpd-tomcat-cluster/
    drwxr-xr-x  7 root   root        4096 Aug  5 05:27 .git/
    drwxr-xr-x  4 root   root        4096 Aug  5 07:18 .m2/
    -rw-r--r--  1 root   root         983 Oct 24  2022 microsoft.asc
    -rw-r--r--  1 root   root         983 Oct 24  2022 microsoft.asc.1
    drwxr-xr-x  3 root   root        4096 Aug 12 13:19 oracle/
    drwxr-xr-x  2 root   root        4096 Aug 10 22:51 oracle-db-data/
    -rw-r--r--  1 root   root         161 Jul  9  2019 .profile
    -rw-rw-r--  1 master master 128028461 Aug 13 14:52 ROOT.war
    -rwxr-xr-x  1 root   root         157 Aug 14 04:18 setenv.sh*
    drwx------  3 root   root        4096 Aug  5 00:42 snap/
    drwxr-xr-x  6 root   root        4096 Aug  5 07:12 spring-framework-petclinic/
    drwxr-xr-x  9 root   root        4096 Aug  5 07:28 spring-petclinic/
    drwxr-xr-x  9 root   root        4096 Aug  5 07:59 spring-petclinic-docker/
    drwx------  2 root   root        4096 Aug  5 00:42 .ssh/
    -rw-r--r--  1 root   root           0 Aug  6 04:58 .sudo_as_admin_successful
    -rw-r--r--  1 root   root         146 Aug  5 07:28 .testcontainers.properties
    -rw-------  1 root   root        8515 Aug 14 04:20 .viminfo
    -rw-r--r--  1 root   root         177 Aug  6 05:00 .wget-hsts
    -rw-r--r--  1 root   root         659 Aug  6 04:58 wget-log
    -rw-r--r--  1 root   root         659 Aug  6 04:59 wget-log.1
    root@kpismain:~# docker cp ~/setenv.sh tomcat-test:/usr/local/tomcat/bin/
    Successfully copied 2.05kB to tomcat-test:/usr/local/tomcat/bin/
    root@kpismain:~#



# setenv.sh 확인
    
    root@kpismain:~# docker exec -it tomcat-test /bin/bash
    root@007acf94922d:/usr/local/tomcat# cd bin/
    root@007acf94922d:/usr/local/tomcat/bin# ll
    total 428
    drwxr-xr-x 1 root root   4096 Aug 14 04:22 ./
    drwxr-xr-x 1 root root   4096 Jul 25 23:19 ../
    -rw-r--r-- 1 root root  36715 Jul  6 14:43 bootstrap.jar
    -rwxr-xr-x 1 root root  25333 Jul 25 23:19 catalina.sh*
    -rw-r--r-- 1 root root   1664 Jul  6 14:43 catalina-tasks.xml
    -rwxr-xr-x 1 root root   2007 Jul 25 23:19 ciphers.sh*
    -rw-r--r-- 1 root root  25661 Jul  6 14:43 commons-daemon.jar
    -rw-r--r-- 1 root root 214214 Jul  6 14:43 commons-daemon-native.tar.gz
    -rwxr-xr-x 1 root root   1932 Jul 25 23:19 configtest.sh*
    -rwxr-xr-x 1 root root   9110 Jul 25 23:19 daemon.sh*
    -rwxr-xr-x 1 root root   1975 Jul 25 23:19 digest.sh*
    -rwxr-xr-x 1 root root   4327 Jul 25 23:19 setclasspath.sh*
    -rwxr-xr-x 1 root root    157 Aug 14 04:18 setenv.sh*
    -rwxr-xr-x 1 root root   1912 Jul 25 23:19 shutdown.sh*
    -rwxr-xr-x 1 root root   1914 Jul 25 23:19 startup.sh*
    -rw-r--r-- 1 root root  52826 Jul  6 14:43 tomcat-juli.jar
    -rwxr-xr-x 1 root root   5550 Jul 25 23:19 tool-wrapper.sh*
    -rwxr-xr-x 1 root root   1918 Jul 25 23:19 version.sh*
    root@007acf94922d:/usr/local/tomcat/bin#


# echo $SHELL


![image](https://github.com/sangbinlee/install-tomcat/assets/4024414/cac035c1-f4b0-47b7-a750-3a114632d4e1)




# docker 

    
    root@master:~# docker cp ~/setenv.sh tomcat-test:/usr/local/tomcat/bin/
    Successfully copied 2.05kB to tomcat-test:/usr/local/tomcat/bin/
    root@master:~# docker logs --tail -f tomcat-test




# docker run -d --name="tomcat-test" -p 8080:8080 tomcat:8
# docker ps
# docker cp ~/setenv.sh tomcat-test:/usr/local/tomcat/bin/
# docker cp ~/ROOT.war tomcat-test:/usr/local/tomcat/webapps/
# docker exec -it tomcat-test /bin/bash
# curl http://localhost:8080
# docker logs --tail -f tomcat-test

