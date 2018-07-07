# 2st week ARTS
## Algorithm
### [Palindrome Number]

总结


## Review
### 1. [Wine Ratings Prediction using Machine Learning](https://towardsdatascience.com/wine-ratings-prediction-using-machine-learning-ce259832b321)





### 2.[What Happens When a Computer Runs Your Life](https://medium.com/s/futurehuman/what-happens-when-a-computer-runs-your-life-4ba7ec152728)






## Tip
### 1.atom
 上周之前我没有编写过MarkDown格式的文件，GitHub也用的不多，习惯性用了WPS写的文章上传。看大家发的ARTS链接都是直接点进去就可以看的，观察了下发现格式不一样，然后去了解了一下MarkDown格式并下载了atom来使用，花了半天的时间大概摸索出来如何使用，第一次写ARTS费了很大功夫。这次好了很多，下面写一些我在使用过程中遇到的问题和解决办法以及技巧。
 1. 插件：[使用Atom打造无懈可击的Markdown编辑器](http://www.cnblogs.com/fanzhidongyzby/p/6637084.html) 上介绍的几个插件基本够用了
   尤其是markdown-preview-plus 可以预览实时渲染+同步滚动（plus自带滚动不用下markdown-scroll-sync），编写数学公式。
 2. 插入和调整图片：不得不说markdown在插入图片这方面实在是反人类（其他方面都很棒）我需要先把图片保存再按照![]()的格式来插入，还需要写路径，本地路径更改图片地址或者删除本地图片好像会出错，所以地址最好写网上的图片地址，没有网上链接地址的好像可以通过微博的一个功能生成外链，太繁琐了我连试都没有试。好在有插件可以用，markdown-image-paste插件看网上很多人推荐，不过我没有使用成功，不知道是不是我个人原因。不过如果你跟我一样不能使用这款插件，我推荐你使用markdown-imagine-assistant,它不仅可以通过直接拖拽图片的方式在文档中生成图片，而且还可以html格式显示，这刚好解决了我在图片上的第二个问题——排版。现在我可以直接直接拖拽图片生成html，然后顺手更改width，height，margin-left等样式来控制图片大小位置,而且可以用p标签使得两张图片放在一行（我上个ARTS就需要这种情况）。拖拽的图片会默认保存在一个assets文件包中,这也很方便。
 ——后来使用过程中atom右下角出现一个deprecation，不过作者给出了[解决方案](https://github.com/tlnagy/atom-markdown-image-assistant/commit/57330e3d55cdd31941ad790a51b9ed7ba432d245)。更改一行代码就解决了。

    7月5日修改：在群里和大家讨论了一下，发现自己想法的不足之处。立即反思并记录下来。
    1.图片大小的问题。当初看到插入图片的官方格式觉得很烦，虽然知道可以修改宽度等格式，但下意识觉得也很烦，快速找到了看似方便快捷的解决途径（我对html语法很熟悉，所以看到自动生成html语句很开心，根本没有去了解其他的）后来群里伙伴贴了他的方法，我才知道原来这也很方便快捷。
    2.是把图片放到网上生成外链再插入文档好，还是直接放好？这个问题根据不同人需求答案也不同。我当初以为我用的插件是通过把我拖拽的图片生成连接放在网上，然后还保存到本地，因此觉得比较好。后来证明自己太naive了，那只是放在了同文档的一个路径下，不过简便了几步操作。但简便操作的弊端是我上传GitHub也需要将图片文件夹一同上传，这刚好变成了我讨厌的场景。而当初写文档的目的是为了1.提高自己思维能力。2.锻炼自己写作能力。3.与人分享讨论。插入的图片源文件基本不会再用到，因此我之后都会采用生成外链的方式插入图片。
    3.现在使用atom发现在英文切换中文输入法时会卡且常常失败，不知道是不是对中文的支持有问题。


















## Share
