# 初始化安装

1. 准备 U 盘，使用 ventoy 制作启动盘 和 ubuntu镜像
2. 安装操作系统 ubuntu
   1. 设置用户名密码 deepseek/deepseek
   2. 连接WiFi
   3. 更新系统 apt update/apt upgrade
   4. 安装 sudo apt install make net-tools gcc openssh-server
   5. 安装 有线网卡驱动 解压后sudo ./autoinstall
3. ~~安装xrdp开启远程桌面~~
   1. ~~sudo apt install xrdp~~
4. 安装Cockpit管理面板（包含Docker管理）
5. 安装Docket
   1. sudo apt-get install -y\
      apt-transport-https\
      ca-certificates\
      curl\
      software-properties-common\
      gnupg-agent
6. 安装Ollama 和DeepseekR1 模型
   1. [https://community.amd.com/t5/ai/running-llms-locally-on-amd-gpus-with-ollama/ba-p/713266](https://community.amd.com/t5/ai/running-llms-locally-on-amd-gpus-with-ollama/ba-p/713266)
   2. 设置模型不超时
   3.  deepseek@deepseek-System-Product-Name:\~$ cat /etc/systemd/system/ollama.service \[Unit] Description=Ollama Service After=network-online.target

       \[Service] ExecStart=/usr/local/bin/ollama serve User=ollama Group=ollama Restart=always RestartSec=3 Environment="PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin" Environment="OLLAMA\_KEEP\_ALIVE=-1"

       \[Install] WantedBy=default.target deepseek@deepseek-System-Product-Name:\~$
   4.
7. 安装OpenWebUI
8. 配置无线访问接口
   1.  [`sudo apt-get install hostapd dnsmasq`](https://gist.github.com/ExtremeGTX/ea1d1c12dde8261b263ab2fead983dc8)

       \

9. 预制操作系统
   1. 预设IP地址 192.168.2.20
10. 预制OpenWebUI账号
    1. 预设管理员账号 admin@admin.com/admin
11. 检查
    1. 笔记本直连，设置本地IP 192.168.2.30
    2. 重启服务器后
    3. 访问192.168.2.30:8080, 确认OpenWebUI 登录正常
    4. 访问192.168.2.30:9090，确认Cockpit管理面板正常
    5. 通过 ssh 192.168.2.30 确认 ssh端口正常


备份方法

```bash
dd if=/dev/nvme0n1 bs=64K conv=noerror,sync | pv | pigz -c > /home/deepseek/backup/nvme0n1_backup.img.gz
```

恢复方法

```bash
sudo gzip -dc /path/to/backup/nvme0n1_backup.img.gz | sudo dd of=/dev/sda bs=64K conv=noerror,sync status=progress
```
