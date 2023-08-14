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



# ------------------------------------------
# docker 실패 해서 docker compose 로 성공
# docker compose 작업 process
   79  vi Dockerfile
   80  docker build -t tomcat:85 .
   81  docker search tomcat
   82  vi Dockerfile
   83  docker build -t tomcat:85 .
   84  docker images
   85  vi docker-compose.yml
   86  docker compose up -d

# vi Dockerfile
       
    root@master:~# vi Dockerfile
    
        FROM tomcat:8-jdk8-openjdk
        
        RUN apt-get update
        RUN apt-get install -y tzdata
        ENV TZ=Asia/Seoul
        ENV system.mode=dev
        ENV log.location=/usr/local/tomcat/logs/part-zone
            
        CMD ["catalina.sh", "run"]

# docker build
    docker build -t tomcat:85 .

# docker images
       
    root@master:~# docker images
    REPOSITORY                     TAG             IMAGE ID       CREATED         SIZE
    tomcat                         85              ce094b6d81ea   8 minutes ago   569MB
    





# vi docker-compose.yml
    root@master:~# vi docker-compose.yml
 
    version: '3.1'
    services:
      tomcat85:
        image: tomcat:85
        container_name: "tomcat-85"
        environment:
          - system.mode=dev
          - log.location=/usr/local/tomcat/logs/part-zone
        volumes:
          - /root/ROOT.war:/usr/local/tomcat/webapps/ROOT.war
        ports:
          - "8080:8080"

# docker compose up -d
    docker compose down

    
# docker compose logs -f

# docker compose ps
    root@master:~# docker compose ps
    NAME                IMAGE               COMMAND             SERVICE             CREATED             STATUS              PORTS
    tomcat-85           tomcat:85           "catalina.sh run"   tomcat85            7 minutes ago       Up 7 minutes        0.0.0.0:8080->8080/tcp, :::8080->8080/tcp


# docker ps
    
    root@master:~# docker ps
    CONTAINER ID   IMAGE       COMMAND             CREATED         STATUS         PORTS                                       NAMES
    85ccefaf19d2   tomcat:85   "catalina.sh run"   7 minutes ago   Up 7 minutes   0.0.0.0:8080->8080/tcp, :::8080->8080/tcp   tomcat-85
    root@master:~#



# 로컬에서 에러 안나는데 도커 컨테이너에 war 올리면 에러나는 원인 = jdk 버
    root@kpismain:~# docker build -t tomcat:85 .
    [+] Building 32.2s (8/8) FINISHED                                                                                                                                                                                                                                                                                                                                                            docker:default
     => [internal] load .dockerignore                                                                                                                                                                                                                                                                                                                                                                      0.0s
     => => transferring context: 2B                                                                                                                                                                                                                                                                                                                                                                        0.0s
     => [internal] load build definition from Dockerfile                                                                                                                                                                                                                                                                                                                                                   0.0s
     => => transferring dockerfile: 233B                                                                                                                                                                                                                                                                                                                                                                   0.0s
     => [internal] load metadata for docker.io/library/tomcat:8-jdk8-openjdk                                                                                                                                                                                                                                                                                                                               2.7s
     => [auth] library/tomcat:pull token for registry-1.docker.io                                                                                                                                                                                                                                                                                                                                          0.0s
     => [1/3] FROM docker.io/library/tomcat:8-jdk8-openjdk@sha256:19f41f912667dafc90c2136e4fa1958d520b4e99d0b9564beacae9e25c0140de                                                                                                                                                                                                                                                                        24.1s
     => => resolve docker.io/library/tomcat:8-jdk8-openjdk@sha256:19f41f912667dafc90c2136e4fa1958d520b4e99d0b9564beacae9e25c0140de                                                                                                                                                                                                                                                                         0.0s
     => => sha256:19f41f912667dafc90c2136e4fa1958d520b4e99d0b9564beacae9e25c0140de 549B / 549B                                                                                                                                                                                                                                                                                                             0.0s
     => => sha256:d9d4b9b6e964657da49910b495173d6c4f0d9bc47b3b44273cf82fd32723d165 5.16MB / 5.16MB                                                                                                                                                                                                                                                                                                         1.4s
     => => sha256:2068746827ec1b043b571e4788693eab7e9b2a95301176512791f8c317a2816a 10.88MB / 10.88MB                                                                                                                                                                                                                                                                                                       2.3s
     => => sha256:f57aaa638fa54a88b6432a49f569c0fdacb6c3d5b9197cb2c08251dabac7b1b8 2.42kB / 2.42kB                                                                                                                                                                                                                                                                                                         0.0s
     => => sha256:6d9b32a2769b81af0358903513bfb3a5a6b4adf68eddb9723c0a57a77099e01a 14.00kB / 14.00kB                                                                                                                                                                                                                                                                                                       0.0s
     => => sha256:001c52e26ad57e3b25b439ee0052f6692e5c0f2d5d982a00a8819ace5e521452 55.00MB / 55.00MB                                                                                                                                                                                                                                                                                                      20.7s
     => => sha256:9daef329d35093868ef75ac8b7c6eb407fa53abbcb3a264c218c2ec7bca716e6 54.58MB / 54.58MB                                                                                                                                                                                                                                                                                                      18.9s
     => => sha256:d85151f15b6683b98f21c3827ac545188b1849efb14a1049710ebc4692de3dd5 5.42MB / 5.42MB                                                                                                                                                                                                                                                                                                         3.2s
     => => sha256:52a8c426d30b691c4f7e8c4b438901ddeb82ff80d4540d5bbd49986376d85cc9 210B / 210B                                                                                                                                                                                                                                                                                                             3.5s
     => => sha256:8754a66e005039a091c5ad0319f055be393c7123717b1f6fee8647c338ff3ceb 105.92MB / 105.92MB                                                                                                                                                                                                                                                                                                    15.1s
     => => sha256:d5cd98ca0f9b2984eec7452eb3ff1ddbe83bb1111b67316a403975f7c5a2d06d 173B / 173B                                                                                                                                                                                                                                                                                                            15.3s
     => => sha256:b61251acb87bdc8a88168089f564438a2dd2f11344c3b5d82e44878c37780dee 12.33MB / 12.33MB                                                                                                                                                                                                                                                                                                      18.2s
     => => sha256:57bfeaa43ad00070076147061829cff30ad5383258af763a74822225c43a1c54 130B / 130B                                                                                                                                                                                                                                                                                                            18.5s
     => => extracting sha256:001c52e26ad57e3b25b439ee0052f6692e5c0f2d5d982a00a8819ace5e521452                                                                                                                                                                                                                                                                                                              0.9s
     => => extracting sha256:d9d4b9b6e964657da49910b495173d6c4f0d9bc47b3b44273cf82fd32723d165                                                                                                                                                                                                                                                                                                              0.1s
     => => extracting sha256:2068746827ec1b043b571e4788693eab7e9b2a95301176512791f8c317a2816a                                                                                                                                                                                                                                                                                                              0.1s
     => => extracting sha256:9daef329d35093868ef75ac8b7c6eb407fa53abbcb3a264c218c2ec7bca716e6                                                                                                                                                                                                                                                                                                              1.0s
     => => extracting sha256:d85151f15b6683b98f21c3827ac545188b1849efb14a1049710ebc4692de3dd5                                                                                                                                                                                                                                                                                                              0.1s
     => => extracting sha256:52a8c426d30b691c4f7e8c4b438901ddeb82ff80d4540d5bbd49986376d85cc9                                                                                                                                                                                                                                                                                                              0.0s
     => => extracting sha256:8754a66e005039a091c5ad0319f055be393c7123717b1f6fee8647c338ff3ceb                                                                                                                                                                                                                                                                                                              0.8s
     => => extracting sha256:d5cd98ca0f9b2984eec7452eb3ff1ddbe83bb1111b67316a403975f7c5a2d06d                                                                                                                                                                                                                                                                                                              0.0s
     => => extracting sha256:b61251acb87bdc8a88168089f564438a2dd2f11344c3b5d82e44878c37780dee                                                                                                                                                                                                                                                                                                              0.1s
     => => extracting sha256:57bfeaa43ad00070076147061829cff30ad5383258af763a74822225c43a1c54                                                                                                                                                                                                                                                                                                              0.0s
     => [2/3] RUN apt-get update                                                                                                                                                                                                                                                                                                                                                                           2.5s
     => [3/3] RUN apt-get install -y tzdata                                                                                                                                                                                                                                                                                                                                                                2.7s
     => exporting to image                                                                                                                                                                                                                                                                                                                                                                                 0.1s
     => => exporting layers                                                                                                                                                                                                                                                                                                                                                                                0.1s
     => => writing image sha256:bc908d8656e4b144c1d643bd897d5f2230db9d2042c48c4c77e8f6d7f1379d8c                                                                                                                                                                                                                                                                                                           0.0s
     => => naming to docker.io/library/tomcat:85                                                                                                                                                                                                                                                                                                                                                           0.0s
    root@kpismain:~# java -version
    openjdk version "17.0.8" 2023-07-18
    OpenJDK Runtime Environment (build 17.0.8+7-Ubuntu-122.04)
    OpenJDK 64-Bit Server VM (build 17.0.8+7-Ubuntu-122.04, mixed mode, sharing)
    root@kpismain:~# docker exec -it tomcat-85 /bin/bash
    root@1f4117171439:/usr/local/tomcat# java -version
    openjdk version "1.8.0_342"
    OpenJDK Runtime Environment (build 1.8.0_342-b07)
    OpenJDK 64-Bit Server VM (build 25.342-b07, mixed mode)
    root@1f4117171439:/usr/local/tomcat#


# 시스템 재시작시 컨테이너 자동 재시작 세팅
    
    root@master:/etc/systemd/system# docker container ps
    CONTAINER ID   IMAGE       COMMAND             CREATED       STATUS       PORTS                                       NAMES
    85ccefaf19d2   tomcat:85   "catalina.sh run"   3 hours ago   Up 3 hours   0.0.0.0:8080->8080/tcp, :::8080->8080/tcp   tomcat-85
    root@master:/etc/systemd/system# docker ps
    CONTAINER ID   IMAGE       COMMAND             CREATED       STATUS       PORTS                                       NAMES
    85ccefaf19d2   tomcat:85   "catalina.sh run"   3 hours ago   Up 3 hours   0.0.0.0:8080->8080/tcp, :::8080->8080/tcp   tomcat-85
    root@master:/etc/systemd/system# docker update --restart=always tomcat-85
    tomcat-85
    root@master:/etc/systemd/system#




# reboot     
    root@master:/etc/systemd/system# reboot now
    
    Remote side unexpectedly closed network connection
    
    ────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
    
    Session stopped
        - Press <Return> to exit tab
        - Press R to restart session
        - Press S to save terminal output to file

# 컨테이너 자동재시작 확인하기

    
    sangbinlee9@master:~$ sudo su
    [sudo] password for sangbinlee9:
    root@master:/home/sangbinlee9# cd ~
    root@master:~# docker ps
    CONTAINER ID   IMAGE       COMMAND             CREATED       STATUS          PORTS                                       NAMES
    85ccefaf19d2   tomcat:85   "catalina.sh run"   3 hours ago   Up 29 seconds   0.0.0.0:8080->8080/tcp, :::8080->8080/tcp   tomcat-85
    root@master:~#


# container and images
    
    
    root@kpismain:~# docker ps -a
    CONTAINER ID   IMAGE                                        COMMAND                  CREATED       STATUS                     PORTS                                       NAMES
    1f4117171439   tomcat:85                                    "catalina.sh run"        2 hours ago   Up 2 hours                 0.0.0.0:8080->8080/tcp, :::8080->8080/tcp   tomcat-85
    1ba38d36d33b   tomcat:8                                     "catalina.sh run"        7 hours ago   Exited (143) 2 hours ago                                               tomcat-test
    e4a10e897a3c   gvenzl/oracle-xe                             "container-entrypoin…"   2 days ago    Up 2 days                  0.0.0.0:1521->1521/tcp, :::1521->1521/tcp   oracle21
    d015057f7064   wvbirder/database-enterprise:12.2.0.1-slim   "/bin/sh -c '/bin/ba…"   3 days ago    Exited (1) 3 days ago                                                  local_db_2
    2f0135b75d42   mcr.microsoft.com/mssql/server:2019-latest   "/opt/mssql/bin/perm…"   8 days ago    Exited (0) 2 days ago                                                  mssql
    ab8515518d09   docker-httpd-tomcat-tomcat                   "catalina.sh run"        8 days ago    Exited (143) 8 days ago                                                docker-httpd-tomcat-tomcat-1
    01dde4958e2e   docker-httpd-tomcat-httpd                    "apachectl -k start …"   8 days ago    Exited (137) 8 days ago                                                docker-httpd-tomcat-httpd-1
    1560bdb645a3   spring-petclinic-docker-petclinic            "./mvnw spring-boot:…"   9 days ago    Exited (143) 8 days ago                                                spring-petclinic-docker-petclinic-1
    2227f628a554   mysql:8                                      "docker-entrypoint.s…"   9 days ago    Exited (0) 8 days ago                                                  spring-petclinic-docker-mysqlserver-1
    1f01568c1cc4   centos:7                                     "/bin/bash"              9 days ago    Exited (0) 9 days ago                                                  sharp_euler
    4dca7a39b847   mysql:5.7.8                                  "/entrypoint.sh mysq…"   9 days ago    Exited (0) 9 days ago                                                  happy_moore
    980043b72b50   postgres:15.3                                "docker-entrypoint.s…"   9 days ago    Exited (0) 9 days ago                                                  spring-petclinic-postgres-1
    3a70363e9a4b   wvbirder/database-enterprise:12.2.0.1-slim   "/bin/sh -c '/bin/ba…"   9 days ago    Exited (137) 2 days ago                                                local_db
    9f264267c1e4   hello-world                                  "/hello"                 9 days ago    Exited (0) 9 days ago                                                  crazy_wing
    root@kpismain:~# docker compose ps
    NAME                IMAGE               COMMAND             SERVICE             CREATED             STATUS              PORTS
    tomcat-85           tomcat:85           "catalina.sh run"   tomcat-85           2 hours ago         Up 2 hours          0.0.0.0:8080->8080/tcp, :::8080->8080/tcp

    
    root@kpismain:~# docker images
    REPOSITORY                          TAG             IMAGE ID       CREATED         SIZE
    tomcat                              85              bc908d8656e4   3 hours ago     569MB
    docker-httpd-tomcat-httpd           latest          a6e8d262383a   8 days ago      218MB
    docker-httpd-tomcat-tomcat          latest          e6d0a7b8d40b   8 days ago      427MB
    spring-petclinic-docker-petclinic   latest          6a066392b46f   9 days ago      510MB
    mysql                               5.7             92034fe9a41f   11 days ago     581MB
    mysql                               8               54150e9955c4   11 days ago     577MB
    postgres                            15.3            8769343ac885   2 weeks ago     412MB
    tomcat                              8               511ab3e2b780   2 weeks ago     426MB
    gvenzl/oracle-xe                    latest          6e7a49043e84   5 weeks ago     2.87GB
    mcr.microsoft.com/mssql/server      2019-latest     330e92fa0cc2   2 months ago    1.47GB
    testcontainers/ryuk                 0.5.1           ec913eeff75a   2 months ago    12.7MB
    hello-world                         latest          9c7a54a9a43c   3 months ago    13.3kB
    centos                              7               eeb6ee3f44bd   23 months ago   204MB
    wvbirder/database-enterprise        12.2.0.1-slim   27c9559d36ec   5 years ago     2.08GB
    mysql                               5.7.8           adedf30d6136   7 years ago     358MB
    root@kpismain:~#
    
    
    root@kpismain:~# docker container ps
    CONTAINER ID   IMAGE              COMMAND                  CREATED       STATUS       PORTS                                       NAMES
    1f4117171439   tomcat:85          "catalina.sh run"        3 hours ago   Up 3 hours   0.0.0.0:8080->8080/tcp, :::8080->8080/tcp   tomcat-85
    e4a10e897a3c   gvenzl/oracle-xe   "container-entrypoin…"   2 days ago    Up 2 days    0.0.0.0:1521->1521/tcp, :::1521->1521/tcp   oracle21
    root@kpismain:~#





    
    root@kpismain:~# docker container ps -a
    CONTAINER ID   IMAGE                                        COMMAND                  CREATED       STATUS                     PORTS                                       NAMES
    1f4117171439   tomcat:85                                    "catalina.sh run"        3 hours ago   Up 3 hours                 0.0.0.0:8080->8080/tcp, :::8080->8080/tcp   tomcat-85
    1ba38d36d33b   tomcat:8                                     "catalina.sh run"        7 hours ago   Exited (143) 3 hours ago                                               tomcat-test
    e4a10e897a3c   gvenzl/oracle-xe                             "container-entrypoin…"   2 days ago    Up 2 days                  0.0.0.0:1521->1521/tcp, :::1521->1521/tcp   oracle21
    d015057f7064   wvbirder/database-enterprise:12.2.0.1-slim   "/bin/sh -c '/bin/ba…"   3 days ago    Exited (1) 3 days ago                                                  local_db_2
    2f0135b75d42   mcr.microsoft.com/mssql/server:2019-latest   "/opt/mssql/bin/perm…"   8 days ago    Exited (0) 2 days ago                                                  mssql
    ab8515518d09   docker-httpd-tomcat-tomcat                   "catalina.sh run"        8 days ago    Exited (143) 8 days ago                                                docker-httpd-tomcat-tomcat-1
    01dde4958e2e   docker-httpd-tomcat-httpd                    "apachectl -k start …"   8 days ago    Exited (137) 8 days ago                                                docker-httpd-tomcat-httpd-1
    1560bdb645a3   spring-petclinic-docker-petclinic            "./mvnw spring-boot:…"   9 days ago    Exited (143) 8 days ago                                                spring-petclinic-docker-petclinic-1
    2227f628a554   mysql:8                                      "docker-entrypoint.s…"   9 days ago    Exited (0) 8 days ago                                                  spring-petclinic-docker-mysqlserver-1
    1f01568c1cc4   centos:7                                     "/bin/bash"              9 days ago    Exited (0) 9 days ago                                                  sharp_euler
    4dca7a39b847   mysql:5.7.8                                  "/entrypoint.sh mysq…"   9 days ago    Exited (0) 9 days ago                                                  happy_moore
    980043b72b50   postgres:15.3                                "docker-entrypoint.s…"   9 days ago    Exited (0) 9 days ago                                                  spring-petclinic-postgres-1
    3a70363e9a4b   wvbirder/database-enterprise:12.2.0.1-slim   "/bin/sh -c '/bin/ba…"   9 days ago    Exited (137) 2 days ago                                                local_db
    9f264267c1e4   hello-world                                  "/hello"                 9 days ago    Exited (0) 9 days ago                                                  crazy_wing
    root@kpismain:~#
