---
layout: post
category : platform
tags : [java scala squeryl sql]
---
{% include JB/setup %}

目前的carpa系列，都把精力集中到UI一层。这个领域，我们玩了N年，已经接近饱和，在玩也就是小打小闹。而我一直以来想要在数据库这层去做点事情。So, 除了UI，Biz Logic，还有什么呢，不就是DB了吗。

我认为这个层面还是有些工作可以去做。长期的编码经历告诉我

	sql在设计层面存在很大的缺陷

特别的，sql的设计缺乏一些基本的特征：

	* enum类型。这导致了很多硬编码的类型，比如billcode，这些billcode大量存在于代码中，给维护带来困难
	* 封装。存储过程缺乏最基本的同类同组的组织成为麻烦
	* join 的增加，case的存在，导致代码难以阅读
	* 数据词典的分离，导致代码提示，静态编译难以进行，并且可能依赖具体数据库实现
	* 没有考虑到dynamic sql 的拼接导致的语言套语言的问题

sql难以剖析，难以扩展,这也给解决以上问题带来复杂度。我们为了以上问题，也有过一些尝试

	1. rohk sql 。通过宏扩展的方式，提供#if #endif 宏，以参数有值无值的方式达到sql的变换。从而在sql拼接过程中，保持sql代码的完整性。
	2. htsql。完全全新引入的语法，最后编译成为sql。希望引入自己的标准，达成对标准的控制，从而达到对sql 数据库的封装
	3. sqlmaker。c#实现，利用现有c#的语法完成的DSL。
	4. xiwa 的基本信息缓冲，让join不必写了

它们可以解决一部分问题。但是寻找一个更好的sql，依然在路上。

我的希望当然是解决以上sql问题,总结下：

	1. enum
	2. 封装
	3. join cutter
	4. data schema
	5. short-circuit

最后，一定是编译成一个sql。我们还不想直接sql挑战，而是以它为踏脚石。说道实现，我想大家都明白，enum，封装，data schema都是比较容易做的。

真正的困难，依然是——寻找一个替代sql的高级语言。

squeryl 有点味道。


下面的代码，感觉起来是不是超现代呢？

<pre>
	class Artist(val id: Long, val name:String)  {	   
	  def songs = 
	    from(MusicDb.songs)(s => where(s.artistId === id) select(s))
	}
</pre>

之后，我认为black-box 还应该有的内容：

	1. RIA 需要的数据应该是json打包的
	2. 打包了Http server ,Log analyser
