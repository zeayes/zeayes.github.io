---
title: pyenv管理python版本
---

`pyenv`是一个类似于nodejs的`nvm`和ruby的`rvm`的python版本管理工具，它可以让你随意切换python的版本。

### 安装

1. 安装到主目录的`.pyenv`目录下：
``` bash
git clone https://github.com/yyuu/pyenv.git ~/.pyenv
```

2. 设置相应的环境变量
```
cat << EOF >> ~/.bashrc
export PYENV_ROOT="\$HOME/.pyenv"
export PATH="\$PYENV_ROOT/bin:\$PATH"
eval "\$(pyenv init -)"
EOF
```

3. 常用命令
``` bash
pyenv install --list # 查看可安装的版本
pyenv install 2.7.11  # 安装指定版本
pyenv root  # 查看PYENV_ROOT环境变量
pyenv versions # 查看本地安装的python
pyenv update # 更新pyenvg
```

### 自定义源

pyenv安装指定版本的时候，默认的是用官方地址的源，python官方下载地址，貌似被墙了，国内下载特别慢，不过pyenv可以通过`PYTHON_BUILD_MIRROR_URL`环境变量指定下载地址。
``` bash
export PYTHON_BUILD_MIRROR_URL="http://pyenv.qiniudn.com/pythons/"
```
pyenv作者github主页是介绍用这个源，试了下发现这个地址的源好久没更新了。看了下`pyenv install --help`，发现是可以从本地源码直接安装的，首先需要下载源某个版本代码到$PYENV_ROOT/sources/{PYTHON_VERSION}目录下，然后执行：
``` bash
pyenv install -k 2.7.11
```
