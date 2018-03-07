# ArticleList
论文阅读计划
这是一篇来自google的文章，非常贴近工程应用，据称文中的算法应用在youtube的推荐上，比原来的要好。文章讨论的主题也是大家最近比较关注的learning to rank，这项技术在解决top-k推荐问题上很受追捧。文中使用的还是基于矩阵分解思想的factor学习，主要创新点在于提出了几个损失函数，既能使用SGD比较快速地训练模型，又同时强调了top-k推荐列表里k个元素的重要性。另外一个比较有意思的就是提出了一个mean maximum rank的评价指标。
