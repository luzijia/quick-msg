### 名称: quick-msg
### 简介：无需安装Kafka等消息中间件就能使用消息队列的服务。
### 安装说明:
1. 编辑 config.ini
2. 执行 ./qmsg config.php.ini

#### 硬件要求
1. 操作系统：RHEL, CentOS,Ubuntu,macOS 10.13+
2. 软件：glibc 2.12+, x86_64, x86_32
3. 内存：最小1GB以上
4. 本地存储：最小1GB以上
5. 网络：最小百兆网卡

### Producer接口使用说明
```javascript
//向Producer接口写入Json数据
curl -X POST -H "Content-Type: application/json" -d '{"docid": 1, "name": "Product A", "price": 100}' http://10.16.17.8:8082/producer
```

### Php版本的Worker使用说明
```javascript
<?php
// 读取Json数据
$data = file_get_contents("php://stdin");
// 解析json数据
$message = json_decode($data, true);
// 业务逻辑处理
echo "Received message: ";
print_r($message);
```

### Python版本的worker使用说明
```javascript
import sys
import json
// 读取Json数据
data = sys.stdin.readline()
// 解析json数据
// 业务逻辑处理
try:
json_data = json.loads(data)
print(json_data)
except json.JSONDecodeError as e:
    print("Error decoding JSON:", e)
```
### 商务合作
#### 联系邮箱:luzijia@gmail.com
