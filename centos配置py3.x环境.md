Author:si1ent  
Date:12-11  
** 前言：**
系统默认安装一般是python2.7版本，但有些工具就需要py3.x版本以上；  
** 获取资源：**
```python
wget https://www.python.org/ftp/python/3.6.3/Python-3.6.3.tgz 
yum -y install gcc 
yum -y install zlib-devel 
yum -y install openssl-devel

```
** 解压：**
```python
tar -zxvf Python-3.6.3.tgz
```
** 检查并安装python3 **
```python
cd Python-3.6.3
./configure --prefix=/usr/local/python3
```
** 安装make && make install **
```python
make 
make install
```
** 配置python3环境变量：**
```python
ln -s /usr/local/python3/bin/python3 /usr/bin/python3 
（备注：python3可以更换简单字符，例如：py3即可调用python3，如下图所示）
```

```python
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
```

