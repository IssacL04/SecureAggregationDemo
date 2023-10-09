# SecureAggregation

基于"Practical Secure Aggregation for Privacy-Preserving Machine Learning"的协议通信实现，使用python.

需要Flask, socketio and socketIO_client等模块

`pip install Flask`

`pip install socketio`

`pip install socketIO-client`

`pip install numpy`

`pip install flask_socketio`

注意：
1.由于socketIO_client长时间未更新，只能适配pip setuptools 3.1.0;而socketio等模块需要更新到setuptools 3.3.0以上，自动更新会将setuptools更新到62.2.0
所以需要手动修改socketIO_client的setup.py文件，将setuptools版本改为3.1.0;
或者先安装socketIO_client，再安装其他模块.
2.socketio模块安装过程中需要Build wheels,需要C++编译环境支持


# Usage:
## Client side:
### 初始化

`c = secaggclient(host,port)`

### 给予权重数组和数组维度

`c.set_weights(nd_numpyarray,dimensions_of_array)`

### 设定本轮迭代次数

`c.configure(common_base, common_mod)`

### 启动客户端

`c.start()`

## Server side:
### 初始化

`s = secaggserver(host,port,n,k)`

n代表该轮中存活的用户，k代表该轮中需要收集的用户数（即规定的参数t）

### 服务器启动

`s.start()`
