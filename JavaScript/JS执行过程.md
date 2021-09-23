# JS执行过程
## 1. 语法分析阶段
1. 词法分析会把语句分解成词法单元，即 Token。
2. 把 Token 转化成抽象语法树（AST）

## 2. 预编译阶段
预编译发生在 变量声明 和 函数声明，匿名函数 和 函数表达式 不参与预编译。主要是创建执行上下文与声明提升

## 3. 执行阶段
逐行执行 js 代码

# 参考资料
[v8 执行 js 的过程](https://www.zoo.team/article/the-process-of-executing-js-in-v8)
[JavaScript预编译](https://zhuanlan.zhihu.com/p/50236805)