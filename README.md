# learn
我的知识文库
# CodeClub Development Kid

CodeClub基于GitLab进行二次开发，Development Kit也是在官方的Kit上进行了调整和修改。

参考本文档的同时，请一并参考[官方的Development Kit](#gitlab-development-kit)。

## 环境准备

请检查Ruby的版本为 2.1.6+

推荐开发平台为Linux(Ubuntu)，注意不要用root账户进行开发。


```
sudo apt-get install git postgresql libpq-dev phantomjs redis-server libicu-dev cmake g++ nodejs libkrb5-dev golang ed pkg-config
```

检查go语言版本是否高于1.5，否则按照下述方式安装：

```
curl -O --progress https://storage.googleapis.com/golang/go1.5.1.linux-amd64.tar.gz
echo '46eecd290d8803887dec718c691cc243f2175fe0  go1.5.1.linux-amd64.tar.gz' | shasum -c - && \
  sudo tar -C /usr/local -xzf go1.5.1.linux-amd64.tar.gz
sudo ln -sf /usr/local/go/bin/{go,godoc,gofmt} /usr/local/bin/
rm go1.5.1.linux-amd64.tar.gz
```

##

### Clone CodeClub Development Kit 仓库

```
git clone git@code.huawei.com:codeclub/gitlab-development-kit.git
cd gitlab-development-kit
```

### 安装依赖仓库及Gems包

执行 `bundle install` 安装依赖的Gem包

```
bundle install
```

执行make可以clone下GitLab仓库（CodeClub的开发主体），安装Gem包并作简单的配置.

```
make
```


### 安装后

执行

```
bundle install
```
启动 Redis （缓存服务） 和 PostgreSQL （数据库服务）:

```
bundle exec foreman start
```

这个窗口不要关闭，然后新开窗口到gitlab-development-kit的根目录执行：

```
cd gitlab && bundle exec rake db:create dev:setup
bin/rake db:migrate RAILS_ENV=development
注意：如果你是和他人共用开发机器，请修改端口号以免冲突，（默认端口是3000）自定义端口：

```
echo 3001 > port
```

然后运行`./run` 即可启动开发环境

```
./run
