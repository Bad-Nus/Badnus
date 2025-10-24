---
tags:
  - 索引
---
# 前言
$\text{badn}$ ，笔记热爱者，在高一下备受手写笔记的折磨后决定开启数据库，初仅作笔记库，在 $\text{2025-9-5}$ 转型数据库。

#  锚点索引
```dataview
table file.etags as 内容
where file.etags=this.file.etags
where file.name!=this.file.name
```
# 文件内容项
```dataview
task from "待肝项"
```

# 文件属性
- 待办：短期内需要进行完善
- 归档：在短期内不会修改，可以标记归档，方便对未归档的文件进行补全
- 隐私：涉及个人信息
- 公开："归档且非私密文件" 属性的子属性
- ...