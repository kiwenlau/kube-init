##运行步骤

**1. 安装Docker**

参考: [https://docs.docker.com/](https://docs.docker.com/)

**2. 运行Kubernetes集群**

```sh
git clone git@github.com:kiwenlau/kube-init.git
cd kube-init/
sudo ./kube-init.sh
```

**3. 测试kubernetes集群**

```
kubectl create -f pod-nginx.yaml
```

查看pod

```
kubectl get pod
```

当nginx pod的状态由pending变为running时，通过kubectl describe命令获取IP

```
kubectl describe pods/nginx
```

输出，可知niginx pod的IP为**172.17.0.4**

```
Name: nginx
Image(s): nginx
Node: 127.0.0.1/127.0.0.1
Labels: <none>
Status: Running
IP: 172.17.0.4
```

测试nginx

```
curl 172.17.0.4
```

输出

```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```


##参考
1. [Kubernetes: The Future of Cloud Hosting](https://meteorhacks.com/learn-kubernetes-the-future-of-the-cloud)
2. [meteorhacks/hyperkube](https://github.com/meteorhacks/hyperkube)
3. [meteorhacks/kube-init](https://github.com/meteorhacks/kube-init)
