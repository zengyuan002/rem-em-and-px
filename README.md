# 详细讲解css单位px、em、rem的含义以及它们之间的区别 

一、首先介绍一下px

   px就是css中最基本的长度单位了，用px做单位基本上没什么问题，可以做到让页面按套路精确的展现
   
   px是相对于显示器分辨而言的
   
   如果全篇用px布局会暗藏一个蛋疼的问题，就是当用户用ctrl滚页面的时侯(说白了就是ctrl+,ctrl-)，你会发现页面结构产生了不可预知的错乱，因此有砖家倡导使用em替代px....
   
二、接下来介绍一下em

   如果你从上到下阅读批文，你应该已经知道了em出现的原因，下面说说em的特性，简单的讲px是绝对单位，1px就是1px，2px就是2px，以此类推，而em是相对单位，em是相对的基准点就是浏览器的字体大小，浏览器默认字体大小是16px,也就是1em默认等于16px,如果你想给某个文字设定为14px，就这样写font-size:0.875em;样式表都用em来写的话，就可以解决ctrl+,ctrl-时造成的页面错乱问题。
   这时侯有人就会抱怨了，数学是体育老师教育的，除以16我怎么可能算明白，那好办，你可以在根节点上重定义基准号html{font-size:62.5%},此时页面基准字号就是16px*62.5% = 10px,那么此时1em=10px,那么些时14px = 1.4em依此类推

   但是,问题又来了，em准确的说是相对于父节点的字号来计算的，如果自身定义了字号那么就相对自身字号来计算，举例如下:
   
   ```
    html { font-size:100%}
    .box-0 {
         height:1em;//此时height等于16px;
     }
    .box-1 {
        font-size:0.625em;//此时基准字号以变更为16*0.625=10px
        height:1em;//此时实际height等于10px;
    }
    ```
    
    看明白了吧，整个页面内1em并不是一个固定不变的值，1em不停的变换，再加上数学是体育老师教的，这不是自作孽吗。。。没关系，css3为我们引入一个新的单位就是rem可以解决这个问题
    
    三、最后介绍一下主角rem
    
    rem与em一样也是一个相对单位，为了方便理解，我们就理解rem为root
    
    em顾名思义rem只相对跟节点计算，这就是说只要在根节点设定好参考值，那么全篇的1rem都相等，计算方式同em，默认1rem=16px;同理你可以设定html{font-size:62.5%}那么1rem就等于10px,以此类推
    
   声明一下:rem是css3属性，没错!这就是说ie678不支持rem属性，只有chrome、firefox等高富帅支持。那么我们就在ie678中用px做兼容处理，例如：
   
  ```
   .box {
      font-size:14px;
      font-size:0.875em;
   }
 ```

