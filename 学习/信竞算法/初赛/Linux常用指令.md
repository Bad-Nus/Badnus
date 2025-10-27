# 文件目录指令
| 命令 | 介绍 | 常用示例/参数 |
| :--- | :--- | :--- |
| `ls` | 列出目录内容 | `ls -la` (显示所有文件详细信息) |
| `pwd` | 打印当前工作目录的路径 | `pwd` |
| `cd` | 切换目录 | `cd /path` `cd ~` (回家目录) `cd -` (返回上一个目录) |
| `mkdir` | 创建新目录 | `mkdir new_dir` `mkdir -p parent/child` (创建多级目录) |
| `rmdir` | 删除**空**目录 | `rmdir empty_dir` |
| `rm` | 删除文件或目录 | `rm file` `rm -r dir` (递归删除) `rm -rf dir` (**强制删除，极其危险！**) |
| `cp` | 复制文件或目录 | `cp file1 file2` `cp -r dir1 dir2` (复制目录) |
| `mv` | 移动或重命名文件/目录 | `mv oldname newname` `mv file /path/to/dir/` |
| `touch` | 创建空文件或更新文件时间戳 | `touch new_file` |
| `cat` | 连接文件并打印到标准输出 (查看小文件) | `cat file.txt` |
| `find` | 在目录树中递归地**查找文件**，功能强大 | `find /home -name "*.txt"` `find /var/log -size +10M` (找大于 10 M 的文件) |
| `locate` | 通过预建数据库快速查找文件 (速度快，结果可能非最新) | `locate nginx.conf` (需先运行 `updatedb` 更新数据库) |
| `which` | 显示命令的完整路径 (在 `$PATH` 中查找) | `which python` |
| `whereis` | 定位命令的二进制程序、源代码和手册页位置 | `whereis ls` |

# C++指令

| 命令 | 功能描述 | 常用参数及示例 | 考察重点 |
| :--- | :--- | :--- | :--- |
| `g++` | GNU C++ 编译器 | `g++ -o program program.cpp` (编译) `g++ -g program.cpp` (生成调试信息) `g++ -O2 program.cpp` (开启 O 2 优化) | **必考！** 参数 `-o` 的含义（指定输出文件名），理解 `-O2` 优化的作用。 |
| `gcc` | GNU C 编译器 | 同 `g++`，用于编译 C 语言程序。 | 同上。 |
| `./` | 运行当前目录下的可执行文件 | `./program` `./program < data.in` (从文件重定向输入) `./program > result.out` (输出重定向到文件) `./program < data.in > result.out` (同时重定向输入和输出) | **必考！** 重定向 `<`, `>` 的含义和使用是绝对重点！ |
| `time` | 测量命令执行时间 | `time ./program` | 查看程序的运行时间（real, user, sys），用于评估效率。 |