# RAE(recursive autoencoder)
这个模型是将recursive NN结合Autoencoder构成一个无监督的句子转换模型。可以将不定长的句子转换成句子向量。
具体算法如下: 
准备工作：将句子的词训练成词向量 
1. 将句子里面的词的词向量，两两结合，形成一个词向量对 
2. 用这些词向量对去初始化Autoencoder，生成模型和参数 
3. 将句子中邻近的词结合，输入初始化训练的Autoencoder模型，选择还原度最高的两个词生成的隐藏层输出，即x3,x4和对应的y1。 
4. 将y1代替句子中的x3,x4，重复步骤3，直到句子所有词合并完成 
5. 将选出的句子对，即[x3,x4],[x2,y1],[x1,y2]放入模型Autoencoder继续训练，更新参数 
6. 直到所有还原度都大于阈值为止 
7. 保留模型参数，计算句子向量

参考本人博客链接地址：http://blog.csdn.net/qq_26609915/article/details/52119512
