# 2048-terminal
一个在 linux 终端运行的 2048 小游戏。

## 编译
首先确保你有 `ncurses` 库。
```sh
git clone https://github.com/xiao-ming-hub/manim.git
make .
```
编译出来的 `2048-terminal` 就是最终要的，其它东西可以直接删掉。

## 运行
```
2048-terminal <mode> [options]
```

`模式`：可选，有 `play replay sandbox get-example` 四个选项。什么也不填会进入模式选择界面，
`ws/jk/123` 移动光标选择模式，`enter` 进入模式。每个模式有各自的选项。

### `play`
和普通的 2048 一样，`wasd/hjkl` 移动，相同的合并（具体玩法自行百度）。

`u/r` undo/redo，<br/>
`q` 开始/结束录制。开始录制时会提示输入回放文件名，录制到的游戏数据就会写入你刚刚提供的文件名。如果文件已存在会覆盖掉。<br/>
`z` 退出游戏，如果正在录制会自动退出录制。

此模式下的可用选项：<br/>
`--record -r [文件名]` 自动开始录制。<br/>
`--start -s 文件名` 读取回放文件最后一刻的状态，并从此状态开始游戏。<br/>
`--append -a` 配合 `--start` 参数使用。如果有，则自动开始录制，且回放信息追加到回放文件末尾。

### `replay`
回放，通过读取录像文件实现回放功能。
```
2048-terminal replay <file>
```

`p` 开始 / 停止播放<br/>
`f` 下一步<br/>
`b` 上一步<br/>
`q` 加快速度<br/>
`s` 减慢速度<br/>
`z` 退出

此模式下的可用参数：
`--speed=[正整数] -s` 每秒的步数<br/>
`--change-config-file=[文件名] -c` 更改回放文件的默认配置文件<br/>
`--use-config-file=[文件名] -u` 使用指定配置文件打开

### `sandbox`
自定义模式。
```
2048-terminal sandbox <config-file>
```

提供配置文件名，游戏会根据文件名开始游戏。参数同 `play` 模式。**注意：**回放文件会和配置文件绑定，如果配置文件移动了，那么回放文件可能会无法打开。

### `get-example`
生成用于机器学习的样例。
```
2048-terminal get-example <input-file> <output-file>
```
给定回放文件和样例文件。

`--use-config-file=[文件名] -u` 使用指定配置文件读取文件。

