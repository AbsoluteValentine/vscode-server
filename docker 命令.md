# docker
docker run -it --name ahbccontest1.1.2 -p 8082:8080 c7c1e0483125 /bin/bash

docker exec -it c7c1e0483125 /bin/bash

docker build -t bc4contest:pk1.1 .

# 测试代码脚本
exec /opt/verify/verifyPre.sh TestGenerateAddress

# bulid 镜像
cd image
chmod -R 777 dockerfile
cd dockerfile
docker build -t bc4contest:pk1.1 .

# docker 推送到仓库
docker tag bc4contest:pk1.1 192.168.1.21:8881/bc4contest/contest:pk1.1
docker push 192.168.1.21:8881/bc4contest/contest:pk1.1

































            //打印同步进度
			// todo 定时
			syncedNum, _ := blockLst[len(blockLst)-1].(*block.DBlock)
			percentage := (syncedNum.NumberU64() - hs.start + 1) / (hs.end - hs.start + 1) * 100
			log.Info("守护区块同步进度", "start", hs.start, "end", hs.end, "已同步到", syncedNum, "进度", fmt.Sprintf("%v%", percentage))