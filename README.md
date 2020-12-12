# ubuntu20.04 开发环境搭建
## 项目简介
> 本人自用开发环境搭建，不依托于科学上网，联通或电信测试通过

### 1. 首先在设置里的软件和更新的源更换为阿里云

### 2. 安装git/git-gui

```shell
sudo apt-get install git git-gui
```

### 3. 下载erlang和elixir的安装包, 其他版本[可点击此链接下载](https://www.erlang-solutions.com/)
- [erlang](https://github.com/duanzhichao/ubuntu_20.04_development/releases/download/erlang-esl_23.1-1_ubuntu_focal_amd64.deb/erlang-esl_23.1-1_ubuntu_focal_amd64.deb)
- [elxir](https://github.com/duanzhichao/ubuntu_20.04_development/releases/download/elixir_1.11.2-1_ubuntu_focal_all.deb/elixir_1.11.2-1_ubuntu_focal_all.deb)

### 4. 安装erlang和elixir

```shell
sudo apt-get dpkg -i ./erlang...
sudo apt-get install -f
sudo apt-get dpkg -i ./elixir...
sudo apt-get install inotify-tools
```

### 5. 安装postgresql和pgadmin4

```shell
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

sudo apt-get update

sudo apt-get -y install postgresql

sudo apt-get install pgadmin4
```

### 6. 设置postgresql的密码
```shell
sudo su postgres
psql
ALTER USER postgres WITH PASSWORD 'postgres';
\q
exit
```

### 7. 安装curl
```shell
sudo apt-get install curl
```

### 8. 安装nodejs14
```shell
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -

sudo apt-get install nodejs

sudo npm install -g webpack
```

### 9.设置hex和mix的cdn
```shell
export HEX_MIRROR="https://cdn.jsdelivr.net/hex"
export HEX_CDN="https://hexpm.upyun.com"
```

### 9.安装elixir和pheonix相关插件
```shell
mix archive.install hex phx_new 1.5.7
mix local.hex --force
mix local.rebar --force
```