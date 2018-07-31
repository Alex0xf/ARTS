# 4th week ARTS
## Algorithm
### 1.[Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/description/)
Problem Explanation:
Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.
#### Soluction
这种题目肯定用递归方便一点
* 首先排除掉一些特殊情况 如果一个链表为空则直接返回另一个链表
* 如果链表不为空则判断当前的两个链表对应的值哪个比较小，将小的作为最终要返回的链表的首节点，当前节点后移
* 递归调用该方法

```java
public ListNode mergeTwoLists(ListNode l1, ListNode l2){
		if(l1 == null) return l2;
		if(l2 == null) return l1;
		if(l1.val < l2.val){
			l1.next = mergeTwoLists(l1.next, l2);
			return l1;
		} else{
			l2.next = mergeTwoLists(l1, l2.next);
			return l2;
		}
}
```
#### Conclusion
没什么太大的优化空间，题目比较简单。
用好递归算法快很多。

## Review
### 97 Things Every Should Know——1st part
#### [Act with Prudence](https://97-things-every-x-should-know.gitbooks.io/97-things-every-programmer-should-know/content/en/thing_01/index.html)
Whatever you undertake, act with prudence and consider the consequences.
这篇文章说到不要因为想要走捷径就忽略质量，不要拖延不去解决问题。你现在的行为就像跟银行贷款一样在未来需要付利息，拖的时间越久需要承担的后果越可怕。如果非要拖延，最好在下一次意识到这个问题时立刻解决。作者还提到了一个方法 As soon as you make the decision to compromise, write a task card or log it in your issue tracking system to ensure that it does not get forgotten.跟我上篇ARTS提到的自己的方法一样。
回想上周和之前几天，虽然忙是一部分原因，但的确自己意识到了ARTS没有写也拖着不去完成以至于到后面就不想完成。以后的ARTS每部分都具体到一周的哪天。时间多可以多钻研一点，写详细一点，时间少可以列一个框架研究，总之是写给自己看的，没必要写的多花哨，重在内涵。

## Tip
### 1.postman
前段时间我都在忙一个项目，后端需要返回给前端JSON数据。返回的时候我们要测试一下是否得到想要的数据，而且返回的数一大串堆在一起不直观。这时候我有接触到一个应用叫postman，似乎很方便做WEB API和Http请求的调试。
#### Postman是什么
Postman提供功能强大的Web API和HTTP请求的调试，它能够发送任何类型的HTTP请求(GET、POST、PUT、DELETE…)，并且能附带任何数量的参数和Headers。不仅如此，它还提供测试数据和环境配置数据的导入导出，付费的Post Cloud用户还能够创建自己的Team Library用来团队协作式的测试，并能够将自己的测试收藏夹和用例数据分享给团队。

自己摸索了一下，感受到postman可以方便记录调试的历史，更改参数和提交方式，美化JSON格式。但没有感觉到postman有多强，后来还是上网查资料，发现了一个很厉害的博主写的一系列关于postman的介绍，这里分享给大家。需要详细了解的可以点击下面的链接，postman更多好处的是方便测试。
[关于postman的各种详细介绍和运用](https://www.jellythink.com/archives/category/tool-tutorials/postman/page/2)

### 2.CDN
前段时间老是听到CDN这个名词，自己不太懂。什么是CDN？为什么要用？适用哪些场景？

什么是CDN？
CDN即Content Delivery Network，内容分发网络。CDN主要功能是在不同的地点缓存内容，通过负载均衡技术，将用户的请求定向到最合适的缓存服务器上去获取内容，比如说，是北京的用户，我们让他访问北京的节点，深圳的用户，我们让他访问深圳的节点。通过就近访问解决因分布、带宽、服务器性能带来的访问延迟问题，适用于站点加速、点播、直播等场景。

为什么要使用CDN？
主要原因是为了加速网站的访问
其他原因：为了实现跨运营商、跨地域的全网覆盖；保障你的网站安全；异地备援；节约成本投入

适用哪些场景？
1. 网站站点/应用加速
2. 视音频点播/大文件下载分发加速
3. 视频直播加速
4. 移动应用加速

## Share
### [我的算法学习之路](http://lucida.me/blog/on-learning-algorithms/)
这是在网上无意间瞥到的一个帖子，文章写的很实在。看完后感慨颇深。
作者介绍了自己学习数据结构和算法的过程，从一枚小白到逐渐成长成大神的过程，其中介绍了自己学习用的书和方法。看完文章，我觉得作者都是基于（想要达到一个目标——发现自己能力不足——针对目标的要求做出相应实践）这样一个自我提升的过程，其实很多方面都可以套用这种方式。
作者还提到了他的面试三板斧：1.手写代码的能力 2.自证代码段的正确性 3.项目经验
说到算法，作者也是经历了 初学时推崇算法牛逼论——实习后鼓吹算法无用论——读研后再被现实打回算法牛逼论，从而了解到算法的重要性，按作者话来说：算法是一种将有限计算资源发挥到极致的武器。如果觉得算法不重要，那一定是你还没到用到算法的阶段，说到底是你水平不够。
