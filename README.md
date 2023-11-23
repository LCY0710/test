
## 基本结构
fisco文件内为fisco bcos区块链底层部署相关代码，其中包含联盟链相关配置及节点信息和智能合约
webase-deploy文件内为前端可视化区块链相关代码


## 节点部署
在fisco目录下执行下面的指令，生成一条单群组4节点的FISCO链:
	bash build_chain.sh -l 127.0.0.1:4 -p 30300,20200
启动所有节点
	bash nodes/127.0.0.1/start_all.sh
查看每个节点的网络连接数目，以node0为例：
	tail -f nodes/127.0.0.1/node0/log/* |grep -i "heartBeat,connected count"

## 启动控制台
	cd ~/fisco/console && bash start.sh

## 编译智能合约
	cd ~/fisco/console/
	bash contract2java.sh solidity -s contracts/solidity/UserContract.sol -p org.fisco.bcos.asset.contract

## 节点前置服务（WeBASE-Front）搭建

### 拷贝sdk证书文件（build_chain的时候生成的）
将节点所在目录/root/fisco/nodes/127.0.0.1/sdk下的ca.crt、node.crt和node.key文件拷贝到/root/webase-front/conf下

### 服务起停
```
启动： bash start.sh
停止： bash stop.sh
检查： bash status.sh
```

### 修改配置，部署所有服务
	python3 deploy.py installAll

### 访问管理平台
	http://{deployIP}:{webPort}
