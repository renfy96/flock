# mac item2安装与美化

[toc]

现在最主流的方式就是用`Oh My ZSH`+`Powerline`字体+`agnoster`主题+`zsh-syntax-highlighting`语法高亮。

## 1. Item2安装

```bash
brew install iterm2
```

上面命令不能用的，可以结合`brew`篇结合使用

## 2. 安装oh-my-zsh

1. 找一个空文件夹

    ```bash
    cd /Applications/tools/
    mkdir zsh
    cd zsh
    ```

2. 利用wget下载oh my zsh安装包

    ```bash
    wget https://gitee.com/mirrors/oh-my-zsh/raw/master/tools/install.sh
    ```

3. 安装

```bash
chmod 755 install.sh
sh install.sh
```

## 3. 美化

1. 修改主题为`agnoster`

    ```bash
    vi ~/.zhsrc
    # 把ZSH_THEME修改为agnoster
    ```

然后从Profiles>Open Profiles>Edit Profiles>Colors，找到右下角修改主题的地方，随意选择一个自己喜欢的主题即可。
2. 下载字体

```bash
git clone https://github.com/powerline/fonts.git --depth=1
cd fonts
./install.sh
cd ..
rm -rf fonts
```

从```Profiles>Open Profiles>Edit Profiles>Text```修改字体。

## 4. 下载插件

```bash
# 先安装一个必要的工具箱
xcode-select --install

# 修正错误，经典的遇到错误 fuck一下来了
brew install thefuck

# 命令输入提示
brew install zsh-autosuggestions

# 命令行高亮显示
brew install zsh-syntax-highlighting

# 文件夹跳转
brew install autojump
```

安装完成后修改配置文件

```bash
export ZSH="/Users/renfy/.oh-my-zsh"
DEFAULT_USER="renfy"
plugins=(
  git
  pip
  zsh-autosuggestions
  zsh-syntax-highlighting
  autojump
)
source /Users/renfy/.oh-my-zsh/oh-my-zsh.sh
export HOMEBREW_NO_AUTO_UPDATE=true
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
export ZSH_HIGHLIGHT_HIGHLIGHTERS_DIR=/usr/local/share/zsh-syntax-highlighting/highlighters
eval $(thefuck --alias)
```

<b>注意路径</b>

`source .zshrc`刷新环境变量，可能会报错

```bash
# 修复 plugin 'zsh-autosuggestions' not found
git clone https://github.com/zsh-users/zsh-autosuggestions ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions

# 修复 plugin 'zsh-syntax-highlighting' not found
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
```

## 5. 其他

最后再看情况要不要设置下透明度和背景图片
从```Profiles>Open Profiles>Edit Profiles>Window```修改透明度和背景图片。
