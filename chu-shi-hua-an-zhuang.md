# 初始化安装

1. 准备 U 盘，使用 ventoy 制作启动盘 和 ubuntu镜像
2. 安装操作系统 ubuntu
3. 安装xrdp开启远程桌面
4. 安装Cockpit管理面板（包含Docker管理）
5. 安装Docket
6. 安装Ollama 和DeepseekR1 模型
7. 安装OpenWebUI
8. 预制操作系统
   1. 预设IP地址 192.168.2.20
   2. 预设root密码 r00tDeepSeek
9. 预制OpenWebUI账号
   1. 预设管理员账号 admin@admin.com/admin
10. 检查
    1. 笔记本直连，设置本地IP 192.168.2.30
    2. 重启服务器后
    3. 访问192.168.2.30:8080, 确认OpenWebUI 登录正常
    4. 访问192.168.2.30:9090，确认Cockpit管理面板正常
    5. 通过 ssh 192.168.2.30 确认 ssh端口正常
    6. 通过 远程桌面确认 图形界面可以正常访问
