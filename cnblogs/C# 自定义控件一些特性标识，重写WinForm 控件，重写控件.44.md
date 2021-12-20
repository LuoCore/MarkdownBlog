<pre>https://blog.csdn.net/cxu123321/article/details/104812099<br />https://blog.csdn.net/biyusr/article/details/7239911<br /><br /><br /><br />是否显示在属性面板上<br /><span style="font-family: 黑体; font-size: 18px;">[Browsable(</span><span style="color: rgba(0, 0, 255, 1);"><span style="font-family: 黑体; font-size: 18px;">true</span><span style="color: rgba(0, 0, 0, 1);"><span style="font-family: 黑体; font-size: 18px;">)</span><br />属性面板上面的说名<br /><span style="color: rgba(0, 128, 128, 1);"><span style="font-size: 18px; font-family: 黑体;">[Description(</span><span style="color: rgba(128, 0, 0, 1);"><span style="font-size: 18px; font-family: 黑体;">"</span><span style="color: rgba(128, 0, 0, 1);"><span style="font-size: 18px; font-family: 黑体;">控件颜色</span><span style="color: rgba(128, 0, 0, 1);"><span style="font-size: 18px; font-family: 黑体;">"), Category(</span><span style="color: rgba(128, 0, 0, 1);"><span style="font-size: 18px; font-family: 黑体;">"</span><span style="color: rgba(128, 0, 0, 1);"><span style="font-size: 18px; font-family: 黑体;">自定义</span><span style="color: rgba(128, 0, 0, 1);"><span style="font-size: 18px; font-family: 黑体;">"), DefaultValue(</span><span style="color: rgba(128, 0, 0, 1);"><span style="font-size: 18px; font-family: 黑体;">""</span><span style="color: rgba(0, 0, 0, 1);"><span style="font-size: 18px; font-family: 黑体;">)]</span><br /><br />下拉选择需要的属性时可通过枚举来定义需要的值<br />public enum luocore { 你,我,他 }<br /><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; private luocore controleColor;<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Browsable(true)]<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; [Description("控件颜色"), Category("自定义"), DefaultValue("")]<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; public luocore ControleColor<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; get { return controleColor; }<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; set { controleColor = value; }<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br /><br /><br /></span></span></span></span></span></span></span></span></span></span></span></pre>
<h3>ToolboxItem</h3>
<pre></pre>
<p>有没有试过写一个用户控件后，想它不出现在工具箱中，当然有，有时候是控件的Designer部分没有写好或没写，有时候是控件一拖出来就报错，有时候是内部使用的控件，不想别人一引用DLL就出现控件。其它设置方法可以很简单。</p>
<pre></pre>
<ol class="hljs-ln">
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line">ToolboxItem(<span class="hljs-literal">false)]</span></div>
</div>
</li>
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line"><span class="hljs-keyword">public <span class="hljs-class"><span class="hljs-keyword">class <span class="hljs-title">MyPanel : <span class="hljs-type">UserControl</span></span></span></span></span></div>
</div>
</li>
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line">{</div>
</div>
</li>
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line">}</div>
</div>
</li>
</ol>
<pre></pre>
<p>这样就可以了。&ldquo;可恶&rdquo;的用户控件就自动隐藏了，不出现在工具箱中。</p>
<p>&nbsp;</p>
<h3>ToolboxBitmap</h3>
<p>写好一个用户控件后，在工具箱中出来的是一个蓝色的齿轮，这就不是很漂亮了，也不能够直观地表达自己的意图。如果更不幸的你的控件的名称好难认的话，其它的开发者会很麻烦的。怎样才能让用户控件在工具箱中显示不同的图标呢?</p>
<ol class="hljs-ln">
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line">ToolboxBitmap(typeof(System.Windows.Forms.Panel))]</div>
</div>
</li>
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line"><span class="hljs-keyword">public <span class="hljs-class"><span class="hljs-keyword">class <span class="hljs-title">MyPanel : <span class="hljs-type">UserControl</span></span></span></span></span></div>
</div>
</li>
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line">{</div>
</div>
</li>
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line">}</div>
</div>
</li>
</ol>
<p>这样就可以了，表示你所做的用户控件使用的图标是Panel的图标。<br /> 如果不想用系统的图标，要使用自己的图标，可以这样</p>
<ol class="hljs-ln"><ol class="hljs-ln">
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line">[ToolboxBitmap(typeof(MyPanel), <span class="hljs-string">"WindowsApplication1.Images.MyPanel.bmp")]</span></div>



</div>



</li>
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line"><span class="hljs-keyword">public <span class="hljs-class"><span class="hljs-keyword">class <span class="hljs-title">MyPanel : <span class="hljs-type">UserControl</span></span></span></span></span></div>



</div>



</li>
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line">{</div>



</div>



</li>
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line">}</div>
<div class="hljs-ln-line">不过，一定要注意路径，<code>WindowsApplication1.Images.MyPanel.bmp</code>表示，解决方案是<code>WindowsApplication1</code>，目录是<code>Images</code>，文件名是<code>MyPanel.bmp</code>，同时，这个图片必须是&ldquo;嵌入的资源&rdquo;（点击文件,右键,属性,有一个文件属性,其中,在生成操作中,可以选择<code>"嵌入的资源"</code>）</div>
<div class="hljs-ln-line">&nbsp;</div>
<div class="hljs-ln-line">&nbsp;</div>
<div class="hljs-ln-line">&nbsp;</div>
<div class="hljs-ln-line">
<h3>DesignerSerializationVisibility</h3>
<p>表示，是否在*.Designer.cs文件中将设置的代码写出来，也就是是否要实现序列化。默认为<br /><code>[DesignerSerializationVisibility(DesignerSerializationVisibility.Visible)]</code>表示需要实现序列化。<br /> 如果设置为hidden：</p>
<ol class="hljs-ln">
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line">        [<span class="hljs-meta">DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]</span></div>



</div>



</li>
<li>
<div class="hljs-ln-code">
<div class="hljs-ln-line">        <span class="hljs-keyword">public List&lt;Person&gt; Persons { <span class="hljs-keyword">get; <span class="hljs-keyword">set; }</span></span></span></div>



</div>



</li>



</ol>
<ul>
<li>1</li>
<li>2</li>



</ul>
<p>将不会被序列化：<br /><img src="https://img-blog.csdnimg.cn/20190212184704321.png" alt="在这里插入图片描述" /><br /> 如果自定义控件中有些属性不需要显示在属性面板或者不需要序列化时，建议hidden掉</p>


</div>



</div>



</li>



</ol></ol>
<pre><span style="color: rgba(0, 0, 255, 1);"><span style="color: rgba(0, 0, 0, 1);"><span style="color: rgba(0, 128, 128, 1);"><span style="color: rgba(128, 0, 0, 1);"><span style="color: rgba(128, 0, 0, 1);"><span style="color: rgba(128, 0, 0, 1);"><span style="color: rgba(128, 0, 0, 1);"><span style="color: rgba(128, 0, 0, 1);"><span style="color: rgba(128, 0, 0, 1);"><span style="color: rgba(128, 0, 0, 1);"><span style="color: rgba(0, 0, 0, 1);">&nbsp;<br /><br />https://www.cnblogs.com/qingtianhua/p/3524526.html<br /></span></span></span></span></span></span></span></span></span></span></span></pre>
<h1 class="postTitle"><a id="cb_post_title_url" class="postTitle2 vertical-middle" href="https://www.cnblogs.com/qingtianhua/p/3524526.html">EditorBrowsable特性 控制智能提示 </a></h1>
<pre></pre>
<div class="postBody">
<div id="cnblogs_post_body" class="blogpost-body blogpost-body-html">
<p>[EditorBrowsable(EditorBrowsableState.Never)]<br />他的作用是：在编辑器中指定属性或方法的可浏览状态。</p>
<p>EditorBrowsableState.Never的枚举说明是：该属性或方法始终不能在编辑器中浏览。</p>
<p>意思就是说，让使用者在调用的时候无法智能感知出Object默认的方法</p>
<p><span style="line-height: 21px; font-family: Arial; font-size: 14px;"><strong><span style="color: rgba(255, 0, 0, 1);">只有在发布DLL后被人引用才可以隐藏方法。同解决方案下的引用无法隐藏</span></strong></span></p>
<p>&nbsp;</p>
<p><span style="line-height: 21px; font-family: Arial; font-size: 14px;"><strong><span style="color: rgba(255, 0, 0, 1);">http://cache.baiducontent.com/c?m=QoVcvCMr0LrQgfs4HZt4T_jI7GGLvjJMVfPlSUenI0UgSBaEjFLn-QzhT_gHReuzPQwohxGTjuzEa2kJBVaCjkUAK9_UhTd2VEOIWtGT9sKmJCS11uistN34-qT2Ys4etlH6oZookRrfT3snrn4J4pFmFLLbxdGEfUr6QzjkxeuaVlLDW4WORE6ULJYGtrjq6o8gu98MsVJISSATJ3jmTK&amp;p=c97dc64ad4934eac58eac16f5a5190&amp;newp=882a9645d18718e90be2963e1c079f231610db2151d4d5146b82c825d7331b001c3bbfb422201107d5ce77630aa84c5eecf53278310923a3dda5c91d9fb4c57479cc7e72&amp;s=cfcd208495d565ef&amp;user=baidu&amp;fm=sc&amp;query=C%23+SRCategoryAttribute+%CE%DE%B7%A8%B7%C3%CE%CA&amp;qid=829b826300061677&amp;p1=9</span></strong></span></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><span style="line-height: 21px; font-family: Arial; font-size: 14px;"><span style="color: #888888;"><a href="https://www.cnblogs.com/qingtianhua/p/3523083.html">523083.html</a> 的作者无关，不对其内容负责。百度快照谨为网络故障时之索引，不代表被搜索网站的即时页面。</span></span></p>
<div id="bd_snap_search"><form action="http://www.baidu.com/s"><input id="bd_snap_kw" type="text" name="wd" maxlength="100" /><span id="bd_snap_btn_wr"> </span></form></div>
<p>&nbsp;</p>
<div><a name="top"></a>
<div id="top_nav" class="navbar forpc">
<ul id="nav_left" class="navbar-list navbar-left">
<li class="navbar-branding"><a title="开发者的网上家园" href="https://www.cnblogs.com/"><img src="https://www.cnblogs.com/images/logo.svg?v=R9M0WmLAIPVydmdzE2keuvnjl-bPR7_35oHqtiBzGsM" alt="博客园Logo" /></a></li>
<li><a href="https://www.cnblogs.com/">首页</a></li>
<li><a href="https://news.cnblogs.com/">新闻</a></li>
<li><a href="https://q.cnblogs.com/">博问</a></li>
<li><a id="nav_brandzone" href="https://brands.cnblogs.com/">专区</a></li>
<li><a href="https://ing.cnblogs.com/">闪存</a></li>
<li><a href="https://edu.cnblogs.com/">班级</a></li>
</ul>
<ul id="nav_right" class="navbar-list navbar-right">
<li><form id="zzk_search" class="navbar-search" action="https://zzk.cnblogs.com/s" method="get"><input id="zzk_search_input" tabindex="3" type="text" name="w" /></form></li>
</ul>
</div>
</div>
<p>&nbsp;</p>
<div id="top_nav" class="navbar forpc">&nbsp;</div>
<p>&nbsp;</p>
<div id="home">
<div id="header">
<div id="blogTitle">
<h1><a id="Header1_HeaderTitle" class="headermaintitle HeaderMainTitle" href="https://www.cnblogs.com/qingtianhua/">青田</a></h1>
</div>
<div id="navigator">
<ul id="navList">
<li><a id="blog_nav_sitehome" class="menu" href="https://www.cnblogs.com/"> 博客园</a></li>
<li><a id="blog_nav_myhome" class="menu" href="https://www.cnblogs.com/qingtianhua/"> 首页</a></li>
<li><a id="blog_nav_newpost" class="menu" href="https://i.cnblogs.com/EditPosts.aspx?opt=1"> 新随笔</a></li>
<li><a id="blog_nav_contact" class="menu" href="https://msg.cnblogs.com/send/%E9%9D%92%E7%94%B0"> 联系</a></li>
<li><a id="blog_nav_rss" class="menu" data-rss="https://www.cnblogs.com/qingtianhua/rss/"></a> 订阅</li>
<li><a id="blog_nav_admin" class="menu" href="https://i.cnblogs.com/"> 管理</a></li>
</ul>
<div class="blogStats">&nbsp;</div>
</div>
</div>
<div id="main">
<div id="mainContent">
<div class="forFlow">
<div id="post_detail">
<div id="topics">
<div class="post">
<h1 class="postTitle"><a name="baidusnap0"></a><a name="baidusnap3"></a><a id="cb_post_title_url" class="postTitle2 vertical-middle" href="https://www.cnblogs.com/qingtianhua/p/3523083.html"> <strong>C#</strong> <strong>Attribute</strong>简介 </a></h1>
<div class="postBody">
<div id="cnblogs_post_body" class="blogpost-body blogpost-body-html">
<p><strong>一 、EventAttribute有：<br />
BrowsableAttribute&nbsp;、CategoryAttribute、DescriptionAttribute、DefaultEventAttribute<br />
PropertyAttribute有：<br />
BrowsableAttribute&nbsp;、CategoryAttribute、DescriptionAttribute、
DefaultPropertyAttribute、DefaultValueAttribute、EditorAttribute&nbsp;、
DesignerSerializationVisibilityAttribute、TypeConverterAttribute、
BindableAttribute、LocalizableAttribute&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<br />
<br />
上述的<strong>Attribute</strong>简明阐述如下：<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BrowsableAttribute：在Property窗口中是否可见。<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;CategoryAttribute：Property或者Event所属的哪个组。<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DescriptionAttribute：Property或者Event的简单描述。<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DefaultEventAttribute：默认Event、。<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DefaultPropertyAttribute：默认Property，选中组件，其Property窗口中默认选中在这个Property上。<br />
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DefaultValueAttribute：Property的默认值，选中组件，其Event窗口中默认选中在这个Event上。</strong></p>
<p><strong>二、</strong></p>
<p>我们来看看在控件设计中有哪些主要用到的设计时<strong>Attribute</strong>。</p>
<p>　　 BrowsableAttribute：描述是否一个属性或事件应该被显示在属性浏览器里。</p>
<p>　　 CategoryAttribute：描述一个属性或事件的类别，当使用类别的时候，属性浏览器按类别将属性分组。</p>
<p>　　 DescriptionAttribute：当用户在属性浏览器里选择属性的时候，description里指定的文本会显示在属性浏览器的下边，向用户显示属性的功能。</p>
<p>　　 BindableAttribute：描述是否一个属性倾向于被绑定。</p>
<p>　　 DefaultPropertyAttribute：为组件指定一个默认的属性，当用户在Form设计器上选择一个控件的时候，默认属性会在属性浏览器里被选中。　　</p>
<p>　　 DefaultValueAttribute：为一个简单类型的属性设置一个默认值。</p>
<p>　　 EditorAttribute：为属性指定一个特殊的编辑器。</p>
<p>　　 LocalizableAttribute：指示一个属性是否能被本地化，任何有这个<strong>Attribute</strong>的属性将会被持久化到资源文件里。　　</p>
<p>　　 DesignerSerializationVisibilityAttribute：指示一个属性是否或者如何持久化到代码里。</p>
<p>　　 TypeConverterAttribute：为属性指定一个类型转换器，类型转换器能将属性的值转化成其它的数据类型。</p>
<p>　　 DefaultEventAttribute：为组件指定一个默认的事件，当用户在form设计其中选择一个控件的时候，在属性浏览器中这个事件被选中。</p>
<p>　　 这些设计时的<strong>Attribute</strong>时很重要的，如果使用的好，将会对用户的使用带来很大的便利。</p>

</div>

</div>

</div>

</div>

</div>

</div>

</div>

</div>

</div>
<p>&nbsp;</p>


</div>


</div>
<pre></pre>