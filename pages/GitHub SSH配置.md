- ### 使用终端创建 SSH key
	- ```node
	  // （将 your_github_email@example.com 替换为您的 Github 账户邮箱）
	  ssh-keygen -t rsa -b 4096 -C "your_github_email@example.com"
	  ```
- ### 根据提示，输入 ssh key 存储的位置和密码，或直接一路回车使用默认设置，等待 ssh key 创建完成。
- ### 将公钥添加到您的 Github 账户中。您可以使用以下命令将公钥复制到剪贴板：
	- ```node
	  pbcopy < ~/.ssh/id_rsa.pub
	  ```
- ### 登录到 Github 网站，打开个人账户界面，点击「Settings」，选择「SSH and GPG keys」，点「New SSH key」，在对话框内粘贴您的公钥内容并保存。