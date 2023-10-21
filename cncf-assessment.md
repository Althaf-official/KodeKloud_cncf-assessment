# KodeKloud_cncf-assessment

### Question 1



## A Dockerfile is available on the controlplane node at the location: /root/nginx. Build a docker image using this Dockerfile with the tag kodekloud/nginx:custom

```ruby
root@controlplane ~/nginx ✖ docker build . -t kodekloud/nginx:custom
Sending build context to Docker daemon  2.048kB
Step 1/3 : FROM nginx:latest
 ---> 1403e55ab369
Step 2/3 : EXPOSE 80
 ---> Running in 1331fa76df98
Removing intermediate container 1331fa76df98
 ---> 1e54c17d432c
Step 3/3 : RUN ["./usr/sbin/nginx"]
 ---> Running in 2c090c208316
2023/10/21 06:23:25 [notice] 1#1: using the "epoll" event method
2023/10/21 06:23:25 [notice] 1#1: nginx/1.23.3
2023/10/21 06:23:25 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) 
2023/10/21 06:23:25 [notice] 1#1: OS: Linux 5.4.0-1106-gcp
2023/10/21 06:23:25 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2023/10/21 06:23:25 [notice] 55#55: start worker processes
2023/10/21 06:23:25 [notice] 55#55: start worker process 56
2023/10/21 06:23:25 [notice] 55#55: start worker process 57
2023/10/21 06:23:25 [notice] 55#55: start worker process 58
2023/10/21 06:23:25 [notice] 55#55: start worker process 59
2023/10/21 06:23:25 [notice] 55#55: start worker process 60
Removing intermediate container 2c090c208316
 ---> 67d90fc9ed83
Successfully built 67d90fc9ed83
Successfully tagged kodekloud/nginx:custom

root@controlplane ~/nginx ➜  
```
