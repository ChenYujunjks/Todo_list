当然可以！我们可以从一个简单的Docker容器运行一个Web服务器的例子开始。我们将使用一个非常流行的Web服务器——Nginx。以下是一个简单的步骤：

### 1. 安装Docker
确保你已经在你的系统上安装了Docker。如果还没有安装，请参考Docker的官方安装指南：[安装Docker](https://docs.docker.com/get-docker/)

### 2. 运行Nginx容器
打开你的终端（命令行）并运行以下命令：

```sh
docker run --name my-nginx -p 8080:80 -d nginx
```

解释：
- `docker run`：这是运行一个新容器的命令。
- `--name my-nginx`：为这个容器指定一个名称，方便管理。
- `-p 8080:80`：将容器的80端口映射到宿主机的8080端口。这样，你可以通过访问`http://localhost:8080`来访问Nginx服务器。
- `-d`：表示容器将在后台运行（detached mode）。
- `nginx`：这是要运行的镜像名称。

### 3. 验证Nginx容器运行
在浏览器中打开`http://localhost:8080`，你应该会看到一个Nginx的欢迎页面，这表示你的Nginx容器已经成功运行并提供服务了。

### 4. 查看运行的容器
你可以使用以下命令来查看正在运行的Docker容器：

```sh
docker ps
```

### 5. 停止和删除容器
如果你想停止并删除这个容器，可以使用以下命令：

```sh
docker stop my-nginx
docker rm my-nginx
```

这会停止并删除你之前创建的Nginx容器。

### 总结
通过以上步骤，你已经成功运行了一个简单的Docker容器，并在其中运行了一个Nginx Web服务器。这是一个很好的开始，帮助你理解Docker容器的基本使用。如果你有更多问题或者想尝试其他示例，请告诉我！