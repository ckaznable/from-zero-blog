---
title: 從零開始的Git
date: 2023-03-06 20:42:24
tags: git
---

當多人一起開發一個項目時，Git 是一個非常有用的工具，它可以幫助團隊協作開發並管理代碼版本。在這篇文章中，我們將從零開始介紹如何使用 Git。

## 安裝 Git

首先，您需要安裝 Git。

### Windows

在 Windows 上安裝 Git 有兩種方法：

#### 1. 下載並安裝 Git for Windows

您可以從 Git 官方網站下載 Windows 版本的 Git，並通過下載運行安裝程序進行安裝。在安裝程序中，您可以自定義 Git 的安裝位置和其他設置。下載頁面網址為：https://git-scm.com/download/win。

#### 2. 使用 winget 包管理器安裝

如果您是windows 11，那應該會內建winget，您可以使用以下命令在 Windows 上安裝 Git：

```shell
winget install --id Git.Git -e --source winget
```

### macOS

在 macOS 上安裝 Git 有三種方法：

#### 1. 通過 Xcode Command Line Tools 安裝

在 macOS 上，您可以使用 Xcode Command Line Tools 安裝 Git。您可以打開終端機應用程序，然後運行以下命令：

```shell
xcode-select --install
```

#### 2. 使用 Homebrew 安裝

如果您已經安裝了 Homebrew 軟件包管理器，您可以使用以下命令在 macOS 上安裝 Git：

```shell
brew install git
```

#### 3. 下載並安裝 Git for macOS

您也可以從 Git 官方網站下載 macOS 版本的 Git，並通過下載運行安裝程序進行安裝。下載頁面網址為：https://git-scm.com/download/mac。

### Linux

在 Linux 上安裝 Git 有多種方法，這裡介紹兩種：

#### 1. 使用包管理器安裝

對於使用 Debian 或 Ubuntu 的用戶，可以使用以下命令在 Linux 上安裝 Git：

```shell
sudo apt-get update
sudo apt-get install git
```

對於使用 Fedora、CentOS 或 Red Hat Enterprise Linux 的用戶，可以使用以下命令安裝 Git：

```shell
sudo yum install git
```

#### 2. 從源代碼編譯和安裝

如果您的 Linux 發行版沒有提供 Git 的包，您可以從源代碼編譯和安裝 Git。您可以從 Git 官方網站下載最新的源代碼包，並按照以下步驟進行編譯和安裝：

```shell
tar -zxf git-2.30.1.tar.gz
cd git-2.30.1
make
sudo make install
```

上述命令假設您已經下載了 Git 的源代碼包，並且已經解壓縮到 git-2.30.1 目錄中。請注意，根據您的系統和 Git 版本的不同，上述命令中的 2.30.1 可能需要相應更改。

除了上述方法外，還有其他的安裝方式。請參考您使用的 Linux 發行版的文檔和支持頁面以獲取更多信息。

安裝完成後，您可以在命令行中運行以下命令來驗證 Git 是否安裝成功：

```shell
git --version
```

如果顯示 Git 的版本號，就代表Git安裝成功了。

## 初次設定

使用 Git 之前，您可能需要在 Git 中設置您的名稱和電子郵件地址，這將用於在提交更改時識別您的身份。您可以使用以下命令設置這些資訊

```shell
# 在這邊填入你的帳號名稱 像是github或gitlab帳號或你希望別人看到的名稱
git config --global user.name "Your Name"
# 填入email
git config --global user.email "your_email@example.com"
```

## 建立 Git 倉庫

在使用 Git 之前，您需要在您的項目目錄中建立一個 Git 倉庫。您可以使用以下命令在當前目錄中建立一個新的 Git 倉庫：

```shell
git init
```

這將創建一個名為 .git 的隱藏目錄，其中包含 Git 倉庫的所有內容。這將使您的目錄成為 Git 倉庫，您可以開始使用 Git 來管理代碼版本。

## 添加和提交代碼

在您的 Git 倉庫中，您需要將代碼添加到 Git 中，然後提交它們以保存它們的版本。您可以使用以下命令將當前目錄中的所有文件添加到 Git 中：

```shell
git add .
```

這將將所有文件添加到 Git 中的“暫存區”，Git 會跟踪這些文件的更改。

然後，您可以使用以下命令將更改提交到 Git 中：

```shell
git commit -m "Initial commit"
```

這將提交當前更改，並為此次提交添加一個描述。在 Git 中，提交是用於保存代碼版本的重要概念。

## 分支管理

在開發過程中，您可能需要在不破壞現有代碼的情況下進行更改。這時，分支管理是非常有用的。您可以使用以下命令創建一個新分支：

```shell
git branch myfeature
```

這將創建一個名為 myfeature 的新分支，您可以在其中進行更改，而不會影響主分支。使用以下命令切換到新分支：

```shell
git checkout myfeature
```

現在，您可以在新分支中進行更改。完成更改後，您可以使用以下命令將更改合併到主分支中：

```shell
git checkout master
git merge myfeature
```

這將將新分支中的更改合併到主分支中，並且在主分支中保留這些更改。

## 遠程管理

當多人協作開發時，您需要將 Git 倉庫與遠程儲存庫相關聯，以便團隊成員可以共享代碼。您可以使用以下命令將本地 Git 倉庫關聯到遠程儲存庫：

```shell
git remote add origin <remote_url>
```

其中 `<remote_url>` 是遠程儲存庫的 URL，例如 GitHub 或 GitLab 上的項目 URL。這將創建一個名為 origin 的遠程儲存庫，您可以使用以下命令將本地代碼推送到遠程儲存庫：

```shell
git push -u origin master
```

這將把本地的 master 分支推送到遠程儲存庫的 master 分支。 -u 選項是一次性的，它將設置遠程儲存庫 origin 作為默認遠程儲存庫，以便您在後續推送時不必指定遠程儲存庫的名稱。

當其他團隊成員在遠程儲存庫中對代碼進行更改時，您可以使用以下命令從遠程儲存庫中拉取更改：

```shell
git pull origin master
```

這將從遠程儲存庫的 master 分支中拉取更改，並將它們合併到您的本地分支中。

## 總結

在這篇文章中，我們從零開始介紹了 Git 的基本使用方法，包括建立 Git 倉庫、添加和提交代碼、分支管理和遠程管理。學習使用 Git 將有助於您更有效地協作開發和管理代碼版本。這只是 Git 的基礎，還有許多其他強大的功能等待您探索。
