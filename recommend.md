1 Learning to Rank Recommendations with the k-Order Statistic Loss (p245.pdf)
这是一篇来自google的文章，非常贴近工程应用，据称文中的算法应用在youtube的推荐上，比原来的要好。文章讨论的主题也是大家最近比较关注的learning to rank，这项技术在解决top-k推荐问题上很受追捧。文中使用的还是基于矩阵分解思想的factor学习，主要创新点在于提出了几个损失函数，既能使用SGD比较快速地训练模型，又同时强调了top-k推荐列表里k个元素的重要性。另外一个比较有意思的就是提出了一个mean maximum rank的评价指标。

2 A Fast Parallel SGD for Matrix Factorization in Shared Memory Systems (best paper，p249.pdf)
这篇来自台湾国立大学libsvm团队的文章获得了本次大会的best paper。无论文章还是ppt，思路表达得非常清晰饱满。这是一篇偏工程实现的文章，比较适合搭平台的，未必对纯粹做model的算法人员有帮助，但仅仅为了开拓一下视野也值得一看。
基于SGD的矩阵分解的并行化计算有过很多的实践，因为无重叠的(p_u,q_v) pair的更新可以独立进行，所以利用这个特性可以进行并行化。这篇文章针对并行化矩阵分解中存在的locking problem和memory discontinuity问题，提出了一种矩阵分解的高效算法，主要的思路是把评分矩阵分成至少n+1*n+1个block（n是计算节点个数），随机为计算节点分配一个合适的block（解决第一个问题），每个节点内则按user序或item序进行更新（解决第二个问题）。过程比较简单，看文章里地算法流程应该就很明了。最后，秉承这个实验室的一贯作风，他们把自己的方法实现并开源（libMF）。
题外话：这届会议上仍然有很多矩阵分解相关的文章，这些理论性的工作是学术界比较喜欢做的事情，而且也是自netflix prize以来形成的比较有“推荐领域”特色的技术。但个人认为它对数据类型和稠密程度有一定的要求（netflix prize提供的数据稠密度在1%左右，算很稠密了，并且是1-5分的分值预测问题，所以SVD会比较容易得到好的效果），且容易碰到cold-start问题，使用过程中需要相当谨慎。但一直以来（包括这次会议）也有不少把这项技术用于0-1无负面反馈的数据（实际中更多碰到的就是这种0-1的top-k推荐问题），可以仔细实践一下，再下定论。
