﻿#美团面试总结

标签（空格分隔）： 面试经验

---
9月20左右笔试的，美团的笔试相对来说还比较容易，很多都是刷过的题，不过听说另外一套卷子的笔试题很难，过了一天通知9月23号下午3点去艾维尔酒店面试，美团的面试一直听说很难，整个面试过程大概持续了4个小时，进去后看见每个面试官跟前的一厚沓纸就挺有压力的，面试的环境是一对一，但是在一个房间里全部都是面试的人，位置比较挤，当然，实际面试中你是听不到别人在说什么的，美团也面到了终面，接下来分享下经验。
##一面:

 1. 美团笔试题，股票问题，获取最佳的买卖股票时间点，求出买卖股票的点。
居然没有什么自我介绍，一上来就拿着我那个笔试题看了看，这个基本就是考察笔试题做的情况的，没什么多说的。
 
 2. 项目问题，怎么做的定位加范围判断，具体核心判断手写
简单的做了下自我介绍，里面涉及到一个商家定位系统，要做坐标抽的x，y轴相加判断，这里的代码面试官要求写一下，有点类似于重载运算符，但是java不支持，所以用hashmap来实现。写完后看了眼面试官，看了遍就没说什么。
 3. Mybatis的数据映射session和Connection之间的关系，Connection和Resourcedata之间的关系
看了会我的简历又问我，你用过Mybatis，然后就问了两个问题，这块没什么说的，Mybatis的源码级问题。

 4. 数据库sql语句，写出两个表联合查询最大值，要去重，对sql语句进行优化，子查询的子查询
问题是就是A、B、C是3张表，以C表为条件的数据查B表，然后再以B表为条件的数据查出A表，就是子查询的子查询，这里有一个关键点就是涉及到的数据是有重复的，所以考察了distinct的用法，同时分组后进行排序，不算复杂，但是要细心。

 5. 面试官手撸代码，下面哪个sql语句会用到索引，select a,b,c,d,e from A where a = "1", b = "1", c = "1";建立一个abc的索引会用到吗
 这里他一开始的问题是select * from A where a = "1", b = "1", c = "1"会用到吗，我说肯定不会啊，用了'*'怎么会用到索引,然后他又换成了组合索引，这就会用到了，我还给他对比了组合索引和单独建索引的区别，涉及到一些B+树，聚集索引非聚集索引的知识。

 6. hashmap的底层实现结构，具体到每一个方法，put，get，重点index方法,手撸
终于问到hashmap，这个是我的强项，一会就写完了，问了一些初始化负载因子的问题后，又讨论了一下效率问题，主要是resize的时候效率的损失，我给他说要是预先知道大小最好直接建一个足够大的，减少它resize的次数。

 7. String的equals方法和Object的equals方法区别
这个问题是从上面的hashmap引过来的，问题就是这里你的index方法使用hashcode算的，如果是自定义类hashcode是用地址算的，那么hashmap怎么通过这个找到他的值，因为我说了平时都用String来作为他的key值，所以让对比了String里的equals和object中的equals方法，最后说了类里面要重写hashcode方法，遗憾的是，我都是用编辑器自动生成的，所以当时没有写出来。

 8. AJAX怎么做的刷新数据，核心地方思路，长连接怎么hold住的
ajax轮询问题，涉及到http协议，tcp协议等，及时用ajax过一段时间发送一个空包，后台要去检测，当包里有数据了处理返回，这次连接结束，下一次ajax再发送空包打开并hold连接，重复上面的步骤。

 9. synchronized的锁用法，锁框架(没答出来)
当时我渣渣的多线程，只知道synchronized的用法，面试官问到多线程时，我只敢说会用，就把synchronized最简单的2中用法说了一遍，面试官也没多问，然后问了我一个问题，你知道有什么锁框架吗？这个我还真不知道，后来回来查了一下，感觉他要问我的就是fork/join框架
 
##一面总结：
美团的一面简直就是我面的最难的，基本全程都在写，不是你写就是面试官给你出题写，问的深度广度都还可以，有一些问题确实没有回答好，多线程不好的劣势一下就体现出来了，包括很多编译器帮你做的事情，比如hashcode方法，因为一次都没写过，所以真让写的时候完全不能写出来。所以java的学习还是尽力不要遗留死角，会扣分的。

##二面:

 1. 自我介绍

 2. 项目介绍，快递系统的AJAX是用来干什么的
感觉像是测试项目是不是你做的

 3. Spring框架介绍,ioc和aop之间是怎么联系的
又是Spring的源码级，这里就不多说了，能说很大一堆，什么接口啦，ioc工厂啦等等等等，反正这里大概说了有20分钟，时间很长。

 4. mysql底层结构,为什么用了b+树，索引结构，优化sql语句，哪些语句会用到索引
这个问题刚好又问到我这了，又从二叉树说起，说到b+树，面试官听了好像特别满意，然后又问了一句sql语句怎么优化，就又从索引啊，分组啊，慢查询啊这些说了一遍，最后他问我哪些sql都会用到索引，嘴贱说了都是通过经验判断的，给我出了一大堆sql让我判断哪些用到了索引。。。。

 5. 手撸代码，i am boy 反转成 boy am i,不能使用split和正则，要求自己设计测试用例通过全部测试
问完那些问题，我以为这面不会写代码了，然后我错了，美团的面试果然每面都要撸代码，不过刚好这个代码我我看过，剑指offer上的，就是不能用split和正则，不过不影响，设置个指针记录位置就可以了。

 6. 性格的优缺点，还发现我简历有错别字。。。丢人了
这个就不多说了，简历上有错别字真的是。。。。。。。。。。。

##二面总结：
个人感觉上二面比一面要简单多了，可能我说的时间比较长面试官问的问题比较少的原因，不过美团面面算法真的是服了，都以为要结束的时候面试官很开心的给我说，我们来做个算法题吧~~~~

##三面:
 1. 现在的研究方向，自己未来的想做的研究方向
又嘴贱说了大数据方向，说完就想抽自己

 2. 关于数据仓库建模的方法，和普通关系型数据库的区别
好吧，果然来了，幸好自己看过一丢丢，给他说了面向主题的三维模型和普通关系型的二维模型

 3. 数据分析的基本方法
这个就完全胡说了，什么数学建模，实地考察，资料统计，正则分析等等

 4. 写一个sql语句（超简单），更新一个数据，考虑更新这个数据都要提前判断的事物（银行取钱过程）
这个就是逻辑思维了，先判断账户类型，今天的额度，余额，然后取钱，最后用了commit提交做一个事物。

 5. 优化这个sql语句（太简单的sql不会优化）
面试官写了个这select a from A where a = '1'（没有注意当时'1'是否带了引号）;让我优化这个sql，我说加索引，他说不是这个意思，让我在这个sql上做优化，想了很久都没想到，后来问了同学，他说如果是带了引号，要去掉这个引号，好吧，当时可能真的没注意，就是注意了我也不知道这个。。。

 6. 分布式情况下，这个sql的判断条件怎么保证执行到sql不会变
从阿里出来后又一次被问到了分布式，不过这次主要是分布式事物，提了5~6种解决方案面试官都否决了，最后都扯到分布式JVM了，不过还是没有提出一个让面试官满意的方案。

 7. 手撸sql语句，又出了个多表联合子查询
居然把分组记错了，group by 记成 order by ，问了我3次我都自信说没错，面试官一说我就醒悟了

 8. 说一件事证明你是一个特别爱思考的人
又说了tcp为什么是3次握手，他还问那断开呢，又BB了会

 9. 打算怎么向你想做的方向努力

 10. 还有什么问题（我问了句面试官是做什么方向的，又问了句java在美团都做些什么，结果面试官给我介绍美团组织结构说了20分钟）

##三面总结：
果然美团的三面是没有hr面的，会穿插一些hr的问题，不过总的还是以技术为主，写代码是不可少的，三面主要写的是sql，可能是因为自己提到了大数据，还有每一面你说的东西都会被记录下来，所以说话的时候一定要注意，重要的东西不要瞎BB。

##总结：
美团的面试果然很有难度，不过现在再想想，其实问的东西又都不是特别难，只要是你平时写过的，面试的时候被问到也不会很怕，面试官人还是很好的，尽量先把你会的东西都问一遍，然后做一些扩展和优化，很遗憾没有收到美团的offer，可能我的个人能力还是差了一些，但是感觉这次面试的经历很重要，可以说，这是我面试过程中，写代码最多的一次。


