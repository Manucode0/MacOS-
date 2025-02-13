macOS配置指南



安装homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

设置环境变量
echo 'export PATH="/opt/homebrew/bin:$PATH"' >> ~/.bash_profile 
source ~/.bash_profile

echo 'export PATH="/opt/homebrew/bin:$PATH"' >> ~/.zshrc   
source ~/.zshrc

echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"

Homebrew设置代理
brew用curl下载，所以给curl挂上socks5的代理即可。
在~/.curlrc文件中输入代理地址即可。
socks5 = "127.0.0.1:1080"



安装git
brew install git

配置git代理
首先需要查看自己梯子节点的端口号[port]

全局http、https代理设置
git config --global http.proxy http://127.0.0.1:[port]
git config --global https.proxy https://127.0.0.1:[port]

只对GitHub进行http、https代理
git config --global http.https://github.com.proxy https://127.0.0.1:[port]
git config --global https.https://github.com.proxy https://127.0.0.1:[port]



全局socks5代理设置
git config --global http.proxy socks5://127.0.0.1:[port]
git config --global https.proxy socks5://127.0.0.1:[port]

只对GitHub进行socks5代理
git config --global http.https://github.com.proxy socks5://127.0.0.1:[port]
git config --global https.https://github.com.proxy socks5://127.0.0.1:[port]

取消代理
git config --global --unset http.proxy
git config --global --unset https.proxy

查看已有配置
git config --global -l