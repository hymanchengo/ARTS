### Algorithm
[电话号码的字母组合](https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/submissions/)

### Review
[Hadoop, MapReduce and Spark – What’s it all about?](https://www.codewall.co.uk/hadoop-mapreduce-and-spark-whats-it-all-about/)
[部分翻译](hadoop.md)

Hadoop也偶尔从同事口中听过这名词，一直不清楚是干嘛的。原来有一个大的生态，虽然看了文章还不是特别理解，

后面抽空跟着例子走一走。
 
### Tip 学习至少一个技术技巧
#### 1, 一个对Java参数传递的误解
在做上述算法题时，我用了一个ArrayList传到一个方法中，

想通过在方法中改变这个ArrayList来获得某个预期结果。下面为该做法的模拟

我期望获得tmp1,temp2这样的结果，最终获得的是origin
```java
public class BlindPoint {
    public static void main(String[] args) {
        List<String> list = new ArrayList<>();
        new BlindPoint().test(list);
        for (String str : list) {
            System.out.println(str);
        }
    }
    public void test(List<String> paramList) {
        paramList.add("origin");
        List<String> tmpList = new ArrayList<String>();
        tmpList.add("tmp1");
        tmpList.add("tmp2");
        paramList = tmpList;
    }
}
```
很容易看出，我平时代码写得少，因此误以为传入了paramList，并将其指向tmpList就能获得想要的结果。

乍一想，感觉没毛病。

细细分析一下:
  paramList形参是实参list的一个值拷贝（拷贝的是参数本身的地址，不是指向的那个对象的地址），
  
  因此paramList最开始和实参list指向的是同一个内存地址，最初添加的origin是能正确影响实参list指向的数据的。
  
  但是之后paramList = tmpList，使得paramList指向了另一个内存地址，它和list指向的数据已经没有任何关系了。因此,
  
  此后paramList中的任何变化都不会反映到list指向的数据中去。最终输出的list数据只有origin一个数据。
  
我想之前我的思维误区在于认为paramList就是list的一个引用，以为它能改变list的指向。

#### 2, dredd使用
最近在试着使用这个API测试框架，通过对Swagger2描述文档的API接口进行编排，利用dredd hooks

来实现一定的测试流程。

本身也在学习中，有兴趣可以参考[官网](https://dredd.org/en/latest/)


### Share 分享一篇有观点和思想的技术文章
[Apache Hadoop Ecosystem](http://blog.newtechways.com/2017/10/apache-hadoop-ecosystem.html)

我简单画了个脑图

![](hadoopeco.jpg)

