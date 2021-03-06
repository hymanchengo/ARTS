### Algorithm
[删除排序数组中的重复项](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)

### Review
文章 [Serverless with Java](https://www.future-processing.com/blog/serverless-with-java/)
      
      这篇文章主要概述了上无服务器的优缺点及讨论了Java语言程序上无服务器的挑战
      
      作者对Java语言是否适合上无服务器的讨论倒不是我关注的一个点。而是serverless这个概念
      
      我是第一次听过，我的理解是serverless也是基于云的一种架构，不是说没有服务器，只是
      
      对于程序编写者和发布者来说无需关心这些这些基础设施，只需关心业务逻辑。另外一点是
      
      之前听说过各种AS，如IAAS,PAAS,SAAS，今天看这篇文章了解还有一个FAAS，技术发展确实很
      
      迅猛。也许Serverless离真正落地还需要很长一段时间，但是听起来还是很酷炫的。不过，那时
      
      估计程序员划分更加明显了，底层的更加底层，专精于基础设施，上层的更上层，写业务逻辑代码，
      
      那时，全栈应该会更加注重的是素养，而不仅仅是技术层面吧？
  
 
### Tip 学习至少一个技术技巧
分享下本周工作遇到问题并解决问题的心得

    简单描述下问题：用模板生成工具生成代码，可是有个项目无法生成，因为自己不是
    
    接触生成工具的第一人，因此便咨询了一下前辈，他说确实在某个版本后，是会出现
    
    这个问题，其实这个信息是很重要的，不是苦思冥想就能得出的，因为这相当于缩小了
    
    排查问题的范围，另外也激起了排查问题的好奇心，因此我便来回尝试多个版本，配合
    
    git代码记录确定可能引起问题的地方，修改，再尝试，期间还开启代码生成工具的debug
    
    模式。这个问题解决了，又出现模板内容问题，但是生成时给出的错误信息很少，很难
    
    排查是哪边出了问题，因此，我采用删文件，定位出现问题的问题，进一步将问题缩小。
    
    直到最后删除代码，定位出错的行，这时结合模板引擎的一些用法，发现问题出在了
    
    模板代码的某些语法和代码引擎的边界符冲突了，导致没有生成出来。
    
**总结**

    事情本身不是关键，但是这里面有几个关键点：一个是沟通，沟通可能得到一些有助于解决问题
    
    的关键信息，当然也有可能带偏，但至少有更多可能性。第二个是一种排查问题的思路，我不能
    
    说我这个排查问题的方式是最优的，但是在不是很了解某个技术或工具的细节时，这种逐步缩小
    
    问题范围，直到定位问题点的思路还是很清晰的。
      

### Share 分享一篇有观点和思想的技术文章
   [什么是Serverless（无服务器）架构？](https://jimmysong.io/posts/what-is-serverless/)
        
        
      
      
