
# unlink

2001 的一篇文章, once upon a free, 介绍了关于glic 当中关于 free 代码存在的一个漏洞. 
具体一点, 就是 malloca 过程当中,管理 malloc 的数据结构, malloc\_chunk , 在从其中的双链表释放的过程当中,对小空间的合并以及链表的重新链接的利用,从而访问以及修改我们不能修改的内容. 
该代码于 glibc 当中,于 2018 年从 unlink 宏修改位了 unlink_chunk 函数, 所以,本视频将介绍的是 2018 年的关于 unlink 的版本, 有兴趣的同学可以去研究最新的代码.

言归正传, 我们将以两个角度来看该问题: 
1. 源代码的结构是什么? 包括 chunk 的结构, unlink 的时候,释放过程以及安全机制.

2. 基于这个结构, 我们看该结构会如何被利用从而可以做到一些逾规之事.