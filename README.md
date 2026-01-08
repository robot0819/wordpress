# wordpress
🚀 WordPress Ubuntu 一键全自动部署脚本
这是一款专为 Ubuntu 系统设计的 WordPress 自动化安装脚本。通过一行命令，即可完成从底层环境（LAMP）到上层应用（WordPress）以及安全防护（SSL）的全量配置。
📋 功能特性
 * 全自动 LAMP 环境：安装 Apache2, MySQL, PHP (含必要扩展)。
 * 智能化配置：
   * 自动生成强健的随机数据库密码。
   * 自动配置 WordPress wp-config.php 并注入官方安全 Salt。
   * 自动优化 PHP 设置（上传限制 240M，内存限制 1024M）。
 * 一键 SSL/HTTPS：集成 Certbot，支持自动申请证书及强制 HTTPS 跳转。
 * 权限优化：自动处理 www-data 用户组权限，确保后台插件/主题安装无阻。
🛠 一键部署指令
在你的 Ubuntu 服务器终端执行以下命令（建议在 root 权限下执行）：

`‌curl -sSO https://raw.githubusercontent.com/robot0819/wordpress/refs/heads/main/ubuntu.sh && sudo bash ubuntu.sh`


📖 部署前准备
 * 系统要求：建议使用全新的 Ubuntu 20.04 或 22.04/24.04 系统。
 * 域名解析：若需开启 SSL，请提前将域名（如 yourdomain.com）解析至服务器 IP。
 * 网络环境：确保服务器可以访问外网以下载必要组件。
🚦 安装交互说明
脚本运行后会依次提示输入：
 * 域名：例如 yuyehd.de。
 * 邮箱：用于 SSL 证书过期提醒。
 * 确认 SSL：输入 y 将自动配置证书（需确保解析已生效）。
📂 关键信息汇总
安装完成后，脚本将输出以下重要数据，请妥善保存：
| 项目 | 默认路径/信息 |
|---|---|
| 网站根目录 | /var/www/html |
| PHP 配置文件 | /etc/php/X.X/apache2/php.ini |
| Apache 访问日志 | /var/log/apache2/wp-access.log |
| Apache 错误日志 | /var/log/apache2/wp-error.log |
| 数据库免密管理 | 脚本已配置 /root/.my.cnf，直接输入 mysql 即可管理 |
⚠️ 安全建议
 * 脚本清理：部署完成后，建议执行 rm ubuntu.sh 以防泄露脚本中生成的初始信息。
 * 防火墙：脚本会自动调用 ufw 开启 Apache 端口，请确保云服务商的安全组也已放行 80 和 443 端口。

