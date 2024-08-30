# gang's dotfiles

每次更换设备都要重新配置，太过愚蠢，所以有了这个仓库。

## about

任何带有`.zsh`扩展名的文件都会自动包含到你的shell中。
任何带有`.symlink`扩展名的文件在你运行`script/bootstrap`时会被符号链接到`$HOME`目录中。

## components

- **bin/**: `bin/`中的任何内容都会被添加到你的`$PATH`中，并在任何地方都可用。
- **topic/\*.zsh**: 任何以`.zsh`结尾的文件都会加载到你的环境中。
- **topic/path.zsh**: 任何名为`path.zsh`的文件会首先加载，预期用于设置`$PATH`或类似的东西。
- **topic/completion.zsh**: 任何名为`completion.zsh`的文件会最后加载，预期用于设置自动补全。
- **topic/install.sh**: 任何名为`install.sh`的文件在你运行`script/install`时会被执行。
  为了避免自动加载，它的扩展名是`.sh`，而不是`.zsh`。
- **topic/\*.symlink**: 任何以`*.symlink`结尾的文件会被符号链接到你的`$HOME`目录中。 
  这样你可以在`dotfiles`中对所有这些文件进行版本控制，但仍然可以在主目录中自动加载这些文件。
  这些文件会在你运行`script/bootstrap`时被符号链接。

## install

Run this:

```sh
git clone https://github.com/CrazyGang97/dotfiles ~/.dotfiles
cd ~/.dotfiles
script/bootstrap
```

这会将`.dotfiles`中的相应文件符号链接到你的主目录中。所有的配置和调整都 在`~/.dotfiles`中完成。

首先要更改的主要文件是`zsh/zshrc.symlink`，它设置了一些在你的特定机器上会有所不同的路径。

`dot`是一个简单的脚本，用于安装一些依赖项，设置合理的macOS默认值，等等。调整这个脚本，并不时运行`dot`以保持你的环境新鲜和最新。你可以在`bin/`中找到这个脚本。