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
# -*- coding: utf-8 -*-
import sys
import json
#读取Json数据
data = sys.stdin.readline()
#解析json数据
#业务逻辑处理
try:
    json_data = json.loads(data)
    print(json_data)
except json.JSONDecodeError as e:
    print("Error decoding JSON:", e)
```

### 性能测试
```javascript
目标机器配置：16G内存 Apple M1芯片
并发100 qps:930.93
[root@centos02 ~]# ab -p post.json -T application/json -n 500 -c 100 http://192.168.1.4:8081/producer
This is ApacheBench, Version 2.3 <$Revision: 1430300 $>
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www.apache.org/

Benchmarking 192.168.1.4 (be patient)
Completed 100 requests
Completed 200 requests
Completed 300 requests
Completed 400 requests
Completed 500 requests
Finished 500 requests


Server Software:
Server Hostname:        192.168.1.4
Server Port:            8081

Document Path:          /producer
Document Length:        11 bytes

Concurrency Level:      100
Time taken for tests:   0.537 seconds
Complete requests:      500
Failed requests:        0
Write errors:           0
Total transferred:      67000 bytes
Total body sent:        98000
HTML transferred:       5500 bytes
Requests per second:    930.93 [#/sec] (mean)
Time per request:       107.419 [ms] (mean)
Time per request:       1.074 [ms] (mean, across all concurrent requests)
Transfer rate:          121.82 [Kbytes/sec] received
                        178.19 kb/s sent
                        300.01 kb/s total

不丢消息，500次写入，消息日志也是500条记录
zijia@192 /tmp % wc -l qmsg-2024-05-28.sys.log
500 qmsg-2024-05-28.sys.log
```


### 商务合作
#### 联系邮箱: luzijia@gmail.com
