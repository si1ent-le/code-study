Author:si1ent  
Date:12-11  
__前言:__  
系统默认安装一般是python2.7版本，但有些工具就需要py3.x版本以上；  
__获取资源:__  
```python
wget https://www.python.org/ftp/python/3.6.3/Python-3.6.3.tgz 
yum -y install gcc 
yum -y install zlib-devel 
yum -y install openssl-devel

```
__解压：__  
```python
tar -zxvf Python-3.6.3.tgz
```
__检查并安装python3:__  
```python
cd Python-3.6.3
./configure --prefix=/usr/local/python3
```
__安装make && make install__  
```python
make 
make install
```
__配置python3环境变量:__  
```python
ln -s /usr/local/python3/bin/python3 /usr/bin/python3 
（备注：python3可以更换简单字符，例如：py3即可调用python3，如下图所示）
```
![alt](https://github.com/si1ent-le/code-study/blob/master/py3.png)
```python
ln -s /usr/local/python3/bin/pip3 /usr/bin/pip3
```

