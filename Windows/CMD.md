# 目录和文件管理命令
- `dir`：显示当前目录下的文件和子目录的列表。
- `cd`：切换目录。
	- `cd folderName`：进入名为 folderName 的子目录
	- `cd ..`：返回上一级目录。
	- `cd /`：进入根目录。
# 系统信息和配置命令
- `netstat`：显示网络统计信息和连接状态。
	- 例如，`netstat -a` 可以显示所有活动的网络连接和监听端口。
	- `netstat -ano | findstr 8080`
