# Homebrew更换国内镜像源

> 在国内的网络环境下使用 Homebrew 安装软件的过程中，可能会长时间卡在 Updating Homebrew ...
>
> 可以通过更改brew的镜像地址实现快速安装

## Brew4.0

#### 临时替换

```shell
# 中科大  https://mirrors.ustc.edu.cn/
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.ustc.edu.cn/brew.git"
export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.ustc.edu.cn/homebrew-core.git"
export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.ustc.edu.cn/homebrew-bottles"
# brew4.x API加速
export HOMEBREW_API_DOMAIN="https://mirrors.ustc.edu.cn/homebrew-bottles/api"
# hide
export HOMEBREW_NO_ENV_HINTS="1"

# 阿里

# 临时替换

export HOMEBREW_INSTALL_FROM_API=1
export HOMEBREW_API_DOMAIN="https://mirrors.aliyun.com/homebrew-bottles/api"
export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/brew.git"
export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/homebrew-core.git"
export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.aliyun.com/homebrew/homebrew-bottles"
brew update

# 重置
unset HOMEBREW_CORE_GIT_REMOTE
```

#### 永久替换

```shell
# 永久替换

# bash 用户
echo 'export HOMEBREW_API_DOMAIN="https://mirrors.aliyun.com/homebrew-bottles/api"' >> ~/.bash_profile
echo 'export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/brew.git"' >> ~/.bash_profile
echo 'export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/homebrew-core.git"' >> ~/.bash_profile
echo 'export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.aliyun.com/homebrew/homebrew-bottles"' >> ~/.bash_profile
source ~/.bash_profile
brew update

# zsh 用户
echo 'export HOMEBREW_API_DOMAIN="https://mirrors.aliyun.com/homebrew-bottles/api"' >> ~/.zshrc
echo 'export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/brew.git"' >> ~/.zshrc
echo 'export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.aliyun.com/homebrew/homebrew-core.git"' >> ~/.zshrc
echo 'export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.aliyun.com/homebrew/homebrew-bottles"' >> ~/.zshrc
source ~/.zshrc
brew update
```



#### 修改镜像地址

> 主要是修改brew几个仓库地址以及配置环境变量即可
>
> 这里以中科大的镜像地址为例

```bash
# 替换 brew.git 仓库地址
  cd "$(brew --repo)" 
  git remote set-url origin https://mirrors.ustc.edu.cn/brew.git
  # 同下面一行命令
  git -C "$(brew --repo)" remote set-url origin https://mirrors.ustc.edu.cn/brew.git 

# 替换 homebrew-core.git 仓库地址
  cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core" 
  git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git
  #
  git -C "$(brew --repo homebrew/core)" remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git

# 替换 homebrew-cask.git 仓库地址
  cd "$(brew --repo)/Library/Taps/homebrew/homebrew-cask"
  git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-cask.git
  # 
  git -C "$(brew --repo homebrew/cask)" remote set-url origin https://mirrors.ustc.edu.cn/homebrew-cask.git

# 替换 homebrew-bottles 访问地址
  vim ~/.zshrc
  export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles
  # 保存后
  source ~/.zshrc
```

#### 主要使用的镜像地址

> 主要是更改这几个下载地址以及环境变量

##### `brew.git homebrew-core.git homebrew-cask.git`镜像

```bash
# 中国科学技术大学（推荐使用）
brew.git:
		https://mirrors.ustc.edu.cn/brew.git
homebrew-core.git:
		https://mirrors.ustc.edu.cn/homebrew-core.git
homebrew-cask.git:
		https://mirrors.ustc.edu.cn/homebrew-cask.git
homebrew-bottles:
		export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles
# 阿里
brew.git:
		https://mirrors.aliyun.com/homebrew/brew.git
homebrew-core.git:  
		https://mirrors.aliyun.com/homebrew/homebrew-core.git
homebrew-cask.git:
		https://mirrors.ustc.edu.cn/homebrew-cask.git
homebrew-bottles:
		export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.aliyun.com/homebrew/homebrew-bottles
# 清华
brew.git:
		https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git
homebrew-core.git:
		https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git
homebrew-cask.git:
		https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-cask.git
homebrew-bottles:
	export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-bottles
# 原镜像也就是github镜像 还原时使用的镜像地址，依次替换就可以
brew.git:
		https://github.com/Homebrew/brew.git
homebrew-core.git:
		https://github.com/Homebrew/homebrew-core.git
homebrew-cask.git:
		https://github.com/Homebrew/homebrew-cask.git
# 还原为官方提供的 homebrew-bottles 访问地址 只需在原本的.zshrc删除即可
vim ~/.zshrc
# 删除或者注释配置的 HOMEBREW_BOTTLE_DOMAIN
source ~/.zshrc
```

