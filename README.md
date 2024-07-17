# Sing-Box-Ubuntu-Actions-Workflow
这是借用 actions 产生的虚拟机网络环境并使用 sing-box + cloudflare tunnel (临时 argo) + vmess 共享网络环境并通过 cloudflared tunnel 加速网络数据从而让我访问国际互联网的临时应急方案  
[![GitHub Workflow Status](https://github.com/UiLgNoD-lIaMtOh/Sing-Box-Ubuntu-Actions-Workflow/actions/workflows/actions.yml/badge.svg)](https://github.com/UiLgNoD-lIaMtOh/Sing-Box-Ubuntu-Actions-Workflow/actions/workflows/actions.yml)![Watchers](https://img.shields.io/github/watchers/UiLgNoD-lIaMtOh/Sing-Box-Ubuntu-Actions-Workflow) ![Stars](https://img.shields.io/github/stars/UiLgNoD-lIaMtOh/Sing-Box-Ubuntu-Actions-Workflow) ![Forks](https://img.shields.io/github/forks/UiLgNoD-lIaMtOh/Sing-Box-Ubuntu-Actions-Workflow) ![Vistors](https://visitor-badge.laobi.icu/badge?page_id=UiLgNoD-lIaMtOh.Sing-Box-Ubuntu-Actions-Workflow) ![LICENSE](https://img.shields.io/badge/license-CC%20BY--SA%204.0-green.svg)
<a href="https://star-history.com/#UiLgNoD-lIaMtOh/Sing-Box-Ubuntu-Actions-Workflow&Date">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=UiLgNoD-lIaMtOh/Sing-Box-Ubuntu-Actions-Workflow&type=Date&theme=dark" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=UiLgNoD-lIaMtOh/Sing-Box-Ubuntu-Actions-Workflow&type=Date" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=UiLgNoD-lIaMtOh/Sing-Box-Ubuntu-Actions-Workflow&type=Date" />
  </picture>
</a>

## 描述
1. 这个项目主要是为了临时能够正常看 youtube 和 google。  
2. 为了实现 actions workflow 自动化运行，需要添加 `GITHUB_TOKEN` 环境变量，这个是访问 GitHub API 的令牌，可以在 GitHub 主页，点击个人头像，Settings -> Developer settings -> Personal access tokens -> Tokens (classic) -> Generate new token -> Generate new token (classic) ，设置名字为 GITHUB_TOKEN 接着要配置 环境变量有效时间，勾选环境变量作用域 repo write:packages workflow 和 admin:repo_hook 即可，最后点击Generate token，如图所示
![image](https://github.com/user-attachments/assets/8f56f08d-ceee-49dd-98c9-7ba011cb54c5)
![image](https://github.com/user-attachments/assets/f42a92e9-f2e6-4424-8196-9802ace4ac5e)
![image](https://github.com/user-attachments/assets/e09dde46-c141-4782-a3c0-ead3939c4df2)
![image](https://github.com/user-attachments/assets/21d2a910-a436-4ae2-972b-6fd05364f29d)

3. 赋予 actions[bot] 读/写仓库权限，在仓库中点击 Settings -> Actions -> General -> Workflow Permissions -> Read and write permissions -> save，如图所示
![image](https://github.com/user-attachments/assets/2faa1a40-9891-4914-ace7-d5d23434b4bb) 

4. 添加 email smtp 服务器域名 `MAILADDR` 在 GitHub 仓库页 -> Settings -> Secrets -> actions -> New repository secret    
5. 添加 email smtp 服务器端口 `MAILPORT` 在 GitHub 仓库页 -> Settings -> Secrets -> actions -> New repository secret    
6. 添加 email smtp 服务器登录账号 `MAILUSERNAME` 在 GitHub 仓库页 -> Settings -> Secrets -> actions -> New repository secret  
7. 添加 email smtp 服务器第三方登陆授权码 `MAILPASSWORD` 在 GitHub 仓库页 -> Settings -> Secrets -> actions -> New repository secret  
8. 添加  email smtp 服务器应该发送邮件位置 `MAILSENDTO` 在 GitHub 仓库页 -> Settings -> Secrets -> actions -> New repository secret
9. 以上 4~9 步流程类似如图所示
![image](https://github.com/user-attachments/assets/b8a825c8-8668-461e-b9b6-541e6c3d01c2)
![image](https://github.com/user-attachments/assets/042da455-64c8-451a-9996-246fe272f218)

10. 转到 Actions -> Sing-Box-Ubuntu-Actions-Workflow 并且启动 workflow，实现自动化  
11. 新目录结构  

        .
        ├── .github                                     # github actions 配置目录  
        │   ├── workflows                               # github actions 配置文件目录  
        │   ├── actions.yml                             # github actions workflow 配置  
        │   └── remove-old-workflow.yml                 # github actions 移除老旧的 workflow  
        ├── set-sing-box.sh                             # 搭建配置 sing-box 脚本  
        └── README.md                                   # 这个是说明文件   

12. 脚本会生成4个文件发送到邮箱，如下图  

        1. result.txt
            a. 包含 vmess 端口转发信息以及共享支持 nekobox 导入链接
        2. VMESS.png
            a. vmess 支持 nekobox 二维码扫描导入
        3. client-nekobox-config.yaml
            a. nekobox 配置文件支持 nekobox 导入
        4. client-sing-box-config.json
            a. sing-box 配置文件支持 sing-box 导入

![image](https://github.com/user-attachments/assets/e7d8aac7-5199-4a65-8865-b813f8284b06)

# 更新
    1. 出于安全考虑还是使用邮箱把发送内容发给自己的邮箱，生成的文件支持 sing-box nekobx 客户端  
    2. 维持的时间还是不稳定，最长维持 44min42s  
    3. 修改发件内容为文本附近形式  
    4. 修改了描述文件，提供详细的描述，方便他人
    5. 添加注释，方便以后的人改写脚本代码
    6. 更新添加优选IP
    7. 生成 vmess 二维码图片和链接方便 nekobox 客户端导入
    8. 生成 yaml 配置文件方便 nekobox 客户端导入

# 缺陷
    1. 经历了许多次无奈，反复折磨，tcp和udp互转，我终于认清了现实，
       在github的actions流环境下，cloudflare 不支持 sing-box 的 udp 数据转发
       我尝试了很多，udp转tcp，tcp转udp，端口监听，我真的尽力了，现在我一点办法也没有，
       唉，我只能用vmess，也许你会问我为什么不买云服务器，我只是想说，太贵了，
       唉，我不想花钱，忍着吧

# 声明
本项目仅作学习交流使用，用于查找资料，学习知识，不做任何违法行为。所有资源均来自互联网，仅供大家交流学习使用，出现违法问题概不负责。  

# 注意
多人 fork 本项目且一起运行 actions 时，可能会导致本人项目被ban掉，所以，你可以创建新项目，把文件复制过去，自己享用

# 感谢&参考  
sing-box: https://sing-box.sagernet.org/   
cloudflared: https://github.com/cloudflare/cloudflared  
CloudflareSpeedTest: https://github.com/XIU2/CloudflareSpeedTest  
使用 email smtp 发送邮件: https://blog.csdn.net/liuyuinsdu/article/details/113878840  
youtube 绵阿羊 在sing-box上安装reality和hysteria2: https://www.youtube.com/watch?v=hbrOxWrGmTc  
文档 绵阿羊 在sing-box上安装reality和hysteria2: https://blog.mareep.net/posts/15209  
github vveg26/sing-box-reality-hysteria2: https://github.com/vveg26/sing-box-reality-hysteria2  
github teddysun/across: https://github.com/teddysun/across  
github 233boy: https://github.com/233boy/sing-box
