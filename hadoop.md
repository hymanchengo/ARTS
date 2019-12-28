# 翻译
[原文链接](https://www.codewall.co.uk/hadoop-mapreduce-and-spark-whats-it-all-about/)
## Hadoop, MapReduce和Spark-都是些啥？

Hadoop是一个开源技术集，促进高分布式处理和大数据集存储

究其核心，Hadoop项目本身仅由几个组件组成。你可以将以下组件视为Hadoop完成高分布式处理的"Hadoop 魔法"方式

  - Hadoop Common
  - HDFS (Hadoop Distributed File System)

以及下面使用MapReduce或其他编程模型为Hadoop构建数据处理程序的方式

  - Hadoop YARN
  - Hadoop MapReduce
 
Hadoop生态还包括许多其他项目，它们具有高度的兼容性，能很好地与Hadoop及其组件协同工作。

Apcahe Spark就是这样的一个项目,它是MapReduce的竞争对手，但它本身也可以使用HDFS，所以它是Hadoop生态的一部分

## 我为什么要关心这些？我能用它们做什么？
既然Hadoop和相关的项目提供了强大的数据集的分布式处理和存储的能力。自然非常的棒，但是落地场景呢？

答案非常的多。这里提供一些例子：

  - 存储大量数据

有些明显，不过几乎每个人都有数据存储需求，而且数据的增长可能会超过最初的预期。HDFS是一个分布式文件系统

扩展它只需要添加额外的集群。

  - 非结构化数据转换为结构化的形式
使用Hadoop提供的编程模型，转换数据集仅仅是一个编写合适程序的场景。使用Hadoop底层的HDFS系统，处理的性能及

规模令人难以置信-能够快速动态地聚合和转换

  - 构建数据湖泊
数据湖泊是一个包含大量原始数据的大型存储库，请求之前以原始格式存储。Hadoop是这类项目的完美候选，它可以存储大量

数据并在运行中快速转换数据。

## MapReduce是什么？
历史以来，Hadoop最常用的编程模型是MapReduce；MapReduce最初是作为谷歌专有技术出现的。但是它的概念和

技术以Apache Hadoop开源项目包含的几种不同的形式获得了新生。

MapReduce是一个编程模型，它将开发易于理解的大数据处理量的复杂任务分解成两个过程：map和reduce

  - Map过程通常在数据缩减和汇总前采取数据过滤和排序操作的形式
  - Reduce过程构成最终的数据处理负载的汇总操作并执行诸如求和，平均，计数和其他类似的组合操作。
  
数据处理负载不仅仅是单个数据集上的一组过程。Hadoop的MapReduce编程模型里有作业的概念，作业可以

被链接或级联在一起从几个不同的MapReduce操作序列，甚至从几个数据集的混合中产生输出。

## Spark是什么？
Spark是一个比MapReduce更容易使用的编程模型。Spark较MapDeduce有更快的数据处理（几乎实时的能力）及内置
的MLlib机器学习。

Spark程序可以使用许多语言编写，有可用的API有Java,Scala,Python和Spark SQL(非常类似于传统SQL)等语言。

虽然使用其他技术编写MapReduce程序是可能的，当然不如Spark中支持得那么好。

Spark程序不使用MapReduce的相同实现作为设计模式，但Spark也有类似的概念。Spark程序通常大量利用DataFrames的概念

组成命名列的分布式数据集合。


  


