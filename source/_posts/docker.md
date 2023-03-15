---
title: 從零開始的Docker
date: 2023-03-10 19:56:49
tags: docker cicd devops
---

Docker 是一種輕量級的虛擬化技術，可用於打包、分發和運行應用程序。本指南將介紹 Docker 的基本概念，並向您展示如何在本地機器上安裝和運行 Docker。

## Docker 基礎概念

### 映像檔（Image）

映像檔是 Docker 的核心概念之一，它是一個只讀模板，可用於創建容器。映像檔可以包含完整的操作系統、應用程序和任何所需的依賴項。

您可以從 Docker 機器上下載現有的映像檔，也可以使用 Dockerfile 創建自己的映像檔。Dockerfile 是一種文本文件，其中包含創建映像檔所需的所有指令。

### 容器（Container）

容器是由映像檔創建的可執行實例。容器包含一個完整的運行環境，包括操作系統、應用程序和所有依賴項。每個容器都是獨立且隔離的，可以在其中運行應用程序，而不會影響主機系統或其他容器。

容器可以啟動、停止、刪除和修改。例如，您可以將容器鏈接到其他容器或外部網絡，以實現通信。

### Dockerfile

Dockerfile 是一種用於創建映像檔的文本文件。它包含創建映像檔所需的所有指令，例如將文件複製到容器中、安裝軟件包和設置環境變數。

以下是一個簡單的 Dockerfile 的範例：

```docker
FROM ubuntu:latest
RUN apt-get update && apt-get install -y python3
COPY my_app.py /
CMD [ "python3", "./my_app.py" ]
```


這個 Dockerfile 創建了一個基於 Ubuntu 最新版本的映像檔，安裝了 Python 3，將 my_app.py 文件從主機複製到容器中，然後運行 my_app.py。

## 安裝 Docker

以下是在不同操作系統上安裝 Docker 的步驟：

### Windows

在 Windows 上安裝 Docker，請依照以下步驟進行：

1. 下載 Docker Desktop for Windows 安裝程式。
2. 運行安裝程式，按照提示進行安裝。
3. 安裝完成

### macOS

在 macOS 上安裝 Docker，請依照以下步驟進行：

1. 下載 Docker Desktop for Mac 安裝程式。
2. 運行安裝程式，按照提示進行安裝。
3. 安裝完成

### Linux

在 Linux 上安裝 Docker，請依照以下步驟進行：

1. 使用以下命令更新包列表：

```shell
sudo apt-get update
```

2. 安裝 Docker 所需的依賴項：

```shell
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release
```

3. 將 Docker 的官方 GPG 金鑰添加到系統：

```shell
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

4. 添加 Docker 的 APT 存儲庫：

```shell
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

5. 使用以下命令安裝 Docker：

```shell
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io
```

## 使用 Docker

安裝完成後，您可以使用以下命令來運行 Docker：

1. 下載映像檔：

```shell
docker pull image_name
```

2. 創建容器：

```shell
docker create --name container_name image_name
```

3. 啟動容器：

```shell
docker start container_name
```

4. 停止容器：

```shell
docker stop container_name
```

5. 刪除容器：

```shell
docker rm container_name
```

6. 列出所有容器：

```shell
docker ps -a
```

7. 列出所有映像檔：

```shell
docker images
```

以上就是從零開始的 Docker 入門指南。希望對您有所幫助！
