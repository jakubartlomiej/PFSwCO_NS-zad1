# Programowanie_full_stack_w_chmurze_obliczeniowej_zadanie_1

3.a docker build -t alpineweb:1.0 .

3.b docker run -it -p 8081:80 alpineweb:1.0 

3.c
```
student@LabVM:~$ docker ps
CONTAINER ID   IMAGE           COMMAND                  CREATED              STATUS              PORTS                                   NAMES
0aa753a340fe   alpineweb:1.0   "lighttpd -D -f /etc…"   About a minute ago   Up About a minute   0.0.0.0:8081->80/tcp, :::8081->80/tcp   ecstatic_pascal
student@LabVM:~$ docker exec -it ecstatic_pascal /bin/sh
/ # cat /var/log/lighttpd/access.log 
2022-06-11 08:57:18 Bartłomiej Jakubowski port 8081
/ # 
```
3.d
```
student@LabVM:~/Documents/zad1$ docker history alpineweb:1.0 
IMAGE          CREATED          CREATED BY                                      SIZE      COMMENT
98fa618dcdbc   10 minutes ago   /bin/sh -c #(nop)  CMD ["lighttpd" "-D" "-f"…   0B        
d89bb01a4f8a   10 minutes ago   /bin/sh -c #(nop)  EXPOSE 80                    0B        
81d2a4e580aa   10 minutes ago   /bin/sh -c echo $(date '+%Y-%m-%d %H:%M:%S')…   53B       
34d6ad53dd6e   10 minutes ago   /bin/sh -c #(nop) COPY file:30f50047eed29863…   1.12kB    
a52068a7e4e4   10 minutes ago   /bin/sh -c #(nop) COPY file:eacc6e06f77e4f34…   740B      
5aa32708f0a6   10 minutes ago   /bin/sh -c apk add php7 php7-fpm php7-opcach…   28.1MB    
1156bca4a472   10 minutes ago   /bin/sh -c apk add --update lighttpd            5.19MB    
65f22837248f   10 minutes ago   /bin/sh -c #(nop)  LABEL MAINTAINER=Bartłomi…   0B        
e04c818066af   2 months ago     /bin/sh -c #(nop)  CMD ["/bin/sh"]              0B        
<missing>      2 months ago     /bin/sh -c #(nop) ADD file:b9eae64dc6ab27fda…   5.59MB   
```
![alt text](/1.png)

4. docker buildx build . -t jakubartlomiej/zad1:lab --platform linux/arm/v7,linux/arm64/v8,linux/amd64 --push
