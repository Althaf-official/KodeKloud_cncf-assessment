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



```ruby
root@controlplane ~/nginx ➜  kubectl get namespaces
NAME              STATUS   AGE
default           Active   3h3m
kube-node-lease   Active   3h3m
kube-public       Active   3h3m
kube-system       Active   3h3m

root@controlplane ~/nginx ➜  kubectl get pods -n development
No resources found in development namespace.

root@controlplane ~/nginx ➜  kubectl describe pod dev-app -n development
Error from server (NotFound): namespaces "development" not found

root@controlplane ~/nginx ✖ kubectl create namespace development
namespace/development created

root@controlplane ~/nginx ➜  ls
Dockerfile

root@controlplane ~/nginx ➜  cd Do
-su: cd: Do: No such file or directory

root@controlplane ~/nginx ✖ touch dev-app-pod.yaml

root@controlplane ~/nginx ➜  vi dev-app-pod.yaml 

root@controlplane ~/nginx ➜  cat dev-app-pod.yaml 
apiVersion: v1
kind: Pod
metadata:
  name: dev-app
  namespace: development
spec:
  containers:
  - name: nginx-container
    image: nginx:latest


root@controlplane ~/nginx ➜  kubectl apply -f dev-app-pod.yaml
pod/dev-app created

root@controlplane ~/nginx ➜  kubectl get pods -n development
NAME      READY   STATUS              RESTARTS   AGE
dev-app   0/1     ContainerCreating   0          30s

root@controlplane ~/nginx ➜  
```


To create a new namespace called "development" and then create a pod named "dev-app" with the "nginx:latest" image inside this namespace, you can use `kubectl` commands. Here's the step-by-step process:

1. **Create the "development" Namespace**:

   Use the following `kubectl` command to create the "development" namespace:

   ```bash
   kubectl create namespace development
   ```

   This command will create a new namespace named "development."

2. **Create the Pod in the "development" Namespace**:

   You can create a pod within the "development" namespace using a YAML configuration file. Here's an example YAML configuration for the "dev-app" pod:

   **dev-app-pod.yaml**:

   ```yaml
   apiVersion: v1
   kind: Pod
   metadata:
     name: dev-app
     namespace: development
   spec:
     containers:
     - name: nginx-container
       image: nginx:latest
   ```

   Save the YAML configuration to a file (e.g., `dev-app-pod.yaml`), and then apply it using the following command:

   ```bash
   kubectl apply -f dev-app-pod.yaml
   ```

   This will create the "dev-app" pod with the "nginx:latest" image inside the "development" namespace.

3. **Check the Pod's Status**:

   You can check the status of the "dev-app" pod within the "development" namespace using the following command:

   ```bash
   kubectl get pods -n development
   ```

   If the pod is running and ready, you should see an entry for "dev-app" with a status of "Running."

Your "development" namespace and the "dev-app" pod using the "nginx:latest" image should now be created. You can verify the status of the pod using the `kubectl` command as mentioned above.




# Question 3



# Expose the dev-app container as a service in such a way that the application would be accessible on port 30081 on the controlplane node.

The application is exposed on port 80 on the container.



