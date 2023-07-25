### 1.查看容器运行日志 

docker logs -f 项目名

### 2.查看创建的容器

docker ps

### 3.查看创建的镜像

docker images

### 4.执行docker-compose文件

docker-compose up -d

### 5.进入一个正在运行的docker容器

docker exec -it container_name /bin/bash

### 6.重启容器（优雅）

docker restart --time=30 container_name

该命令将使用30秒的停机时间重启容器。

### 7.查看容器的详细信息

docker inspect container_name

### 8.删除容器

docker rm -f <containerid>

### 9.删除镜像

docker rmi <imagesID>



Dockerfile 是用于定义 Docker 镜像构建过程的文本文件。它包含了一系列的指令和配置，用于描述如何构建镜像和配置容器环境。

以下是使用 Dockerfile 的一般步骤：

1. 创建 Dockerfile 文件：在项目的根目录下创建一个名为 "Dockerfile"（无文件扩展名）的文件。

2. 编写 Dockerfile 内容：打开 Dockerfile 文件，使用文本编辑器编写镜像构建的指令和配置。Dockerfile 由一系列指令构成，每个指令都对应于镜像构建过程的一个步骤。

3. 编写镜像构建指令：Dockerfile 中的指令根据构建需求和应用程序的特定要求而有所不同。一些常见的指令包括：
   - `FROM`：指定基础镜像，例如 `FROM ubuntu:latest`。
   - `RUN`：运行命令，例如安装软件包、执行编译命令等。
   - `COPY` 或 `ADD`：复制文件或目录到镜像中。
   - `EXPOSE`：指定容器监听的端口号。
   - `CMD` 或 `ENTRYPOINT`：设置容器启动时执行的命令。

4. 构建 Docker 镜像：在 Dockerfile 所在的目录下打开终端或命令行窗口，运行以下命令构建镜像：
   ```
   docker build -t <image_name> .
   ```
   其中 `<image_name>` 是你为镜像指定的名称，`.` 表示使用当前目录中的 Dockerfile 进行构建。Docker 将按照 Dockerfile 中的指令顺序执行构建过程，生成镜像。

5. 运行容器：构建成功后，可以使用以下命令运行容器：
   ```
   docker run -d  -p 8080:80 --name <container_name> <image_name>
   ```
   其中 `<container_name>` 是你为容器指定的名称，`<image_name>` 是你之前构建的镜像名称。这将创建一个新的容器并在其中运行你的应用程序。

以上是一个简单的使用 Dockerfile 构建镜像和运行容器的流程。根据你的具体需求和应用程序的特点，可以进一步扩展和定制 Dockerfile 中的指令和配置。更多关于 Dockerfile 的详细语法和指令，请参考 Docker 官方文档。

yum install -y docker-ce-18.09.0-3.el7 docker-ce-cli-18.09.0-3.el7 containerd.io-1.2.0-3.el7









socket   最关键的一点 配置ServerEndpointExporter      权限放行

















### 10.安装docker

在CentOS系统上安装Docker，可以按照以下步骤进行：

1. 更新系统软件包：

   ```
   plaintextCopy code
   sudo yum update
   ```

2. 安装Docker的依赖软件包：

   ```
   plaintextCopy code
   sudo yum install -y yum-utils device-mapper-persistent-data lvm2
   ```

3. 添加Docker的软件源：

   ```
   plaintextCopy code
   sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
   ```

4. 安装Docker：

   ```
   plaintextCopy code
   sudo yum install docker-ce
   ```

5. 启动Docker服务：

   ```
   plaintextCopy code
   sudo systemctl start docker
   ```

6. 设置Docker开机自启动：

   ```
   plaintextCopy code
   sudo systemctl enable docker
   ```

7. 验证Docker是否成功安装：

   ```
   plaintextCopy code
   sudo docker run hello-world
   ```



1）配置镜像地址：
mkdir /etc/docker
vi /etc/docker/daemon.json
内容如下：
{
"registry-mirrors": ["https://docker.mirrors.ustc.edu.cn"]
}
2）安装docker

yum install -y docker-ce-18.09.0-3.el7 docker-ce-cli-18.09.0-3.el7 containerd.io-1.2.0-3.el7

3)启动docker

sudo systemctl start docker





### 11.安装docker-compose

sudo yum install -y docker-compose