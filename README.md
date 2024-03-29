# ubuntu20.04 开发环境搭建
## 项目简介
> 本人自用开发环境搭建，不依托于科学上网，联通或电信测试通过

### 1. 首先在设置里的软件和更新的源更换为阿里云

### 2. 安装terminator/git/git-gui

```shell
sudo apt-get install -y terminator

sudo apt-get install -y git git-gui
```
### 3.安装erlang和elixir,两种安装方式,任选一样
#### 3.1. 安装包(新版本可能有部分问题，1.13以后), 其他版本[可点击此链接下载](https://www.erlang-solutions.com/downloads/)
- [erlang](https://github.com/duanzhichao/ubuntu_20.04_development/releases/download/erlang-esl_23.1-1_ubuntu_focal_amd64.deb/erlang-esl_23.1-1_ubuntu_focal_amd64.deb)
- [elxir](https://github.com/duanzhichao/ubuntu_20.04_development/releases/download/elixir_1.11.2-1_ubuntu_focal_all.deb/elixir_1.11.2-1_ubuntu_focal_all.deb)
```shell
sudo dpkg -i ./erlang...
sudo apt-get install -f
sudo dpkg -i ./elixir...
sudo apt-get install inotify-tools
```

#### 3.2. 安装erlang和elixir
```shell
wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb && sudo dpkg -i erlang-solutions_2.0_all.deb

sudo apt-get update

sudo apt-get install esl-erlang

sudo apt-get install elixir
```

### 4. 安装postgresql和pgadmin4，如果源没有release文件，可[点击此链接现在对应安装deb包](https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/focal/dists/pgadmin4/main/binary-amd64/)

```shell
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

sudo apt-get update

sudo apt-get -y install postgresql-12

sudo apt-get -y install pgadmin4
```

### 5. 设置postgresql的密码
```shell
sudo su postgres
psql
ALTER USER postgres WITH PASSWORD 'postgres';
\q
exit
```

### 6. 添加普通用户权限,root或hitb
```shell
sudo su postgres
psql
create user <user-name> with password '123456';
alter role <user-name> superuser;
\q
exit
```

### 7. 安装curl
```shell
sudo apt-get -y install curl
```

### 8. 安装nodejs16
```shell
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -

sudo apt-get -y install nodejs

sudo npm install -g webpack pnpm yarn 
```

### 9.设置hex和mix的cdn
```shell
export HEX_MIRROR="https://cdn.jsdelivr.net/hex"

export HEX_CDN="https://hexpm.upyun.com"
```

### 10.安装elixir和pheonix相关插件
```shell
mix archive.install hex phx_new 1.6.0

mix local.hex --force

mix local.rebar --force
```
