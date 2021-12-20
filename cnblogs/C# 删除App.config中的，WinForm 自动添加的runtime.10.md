<p>&nbsp;</p>
<div class="cnblogs_code">
<pre> <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;summary&gt;</span>
        <span style="color: #808080;">///</span><span style="color: #008000;"> 清空App.config节点下的内容
        </span><span style="color: #808080;">///</span> <span style="color: #808080;">&lt;/summary&gt;</span>
        <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;param name="strNode"&gt;&lt;/param&gt;</span>
        <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> AppConfigRemoveChild(<span style="color: #0000ff;">string</span><span style="color: #000000;"> strNode)
        {
            XmlDocument xDoc </span>= <span style="color: #0000ff;">new</span><span style="color: #000000;"> XmlDocument();
            </span><span style="color: #008000;">//</span><span style="color: #008000;">获取可执行文件的路径和名称</span>
            xDoc.Load(System.Windows.Forms.Application.ExecutablePath + <span style="color: #800000;">"</span><span style="color: #800000;">.config</span><span style="color: #800000;">"</span><span style="color: #000000;">);
            </span><span style="color: #0000ff;">using</span> (XmlNodeList xnl = xDoc.SelectSingleNode(<span style="color: #800000;">"</span><span style="color: #800000;">//</span><span style="color: #800000;">"</span>+<span style="color: #000000;"> strNode).ChildNodes) 
            {
                </span><span style="color: #0000ff;">for</span> (<span style="color: #0000ff;">int</span> i = <span style="color: #800080;">0</span>; i &lt; xnl.Count; i++<span style="color: #000000;">)
                {
                    xnl[i].ParentNode.RemoveChild(xnl[i]);
                }
                xDoc.Save(System.Windows.Forms.Application.ExecutablePath </span>+ <span style="color: #800000;">"</span><span style="color: #800000;">.config</span><span style="color: #800000;">"</span><span style="color: #000000;">);
            }
        }</span></pre>
</div>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><span style="color: #ff6600;"><strong><span style="font-family: Microsoft YaHei; font-size: 18pt;">这是参考文章</span></strong></span></p>
<p>https://blog.csdn.net/chunleixiahe/article/details/55504152</p>
<p>&nbsp;</p>
<p>1、test.xml文件内容<br /><br />&lt;?xml version="1.0" encoding="UTF-8"?&gt;<br />&lt;TestList&gt;<br />&nbsp; &lt;test a="" b=""/&gt;<br /><br />&nbsp;&lt;test a="" b=""/&gt;<br />&lt;/TestList&gt;<br /><br />2、实现代码<br /><br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; bool bSuccess = true;<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; while (bSuccess)<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; string strTaskListPath = CommVar.curExecPath + "test.xml";<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; XmlDocument xmlDoc = new XmlDocument();<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; xmlDoc.Load(strTaskListPath);<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; XmlNodeList xnl = xmlDoc.SelectSingleNode("TestList").ChildNodes;<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; int nCount = xnl.Count;<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if (0 == nCount)<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; bSuccess = false;<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; for (int i = 0; i &lt; xnl.Count; i++)<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; xnl[i].ParentNode.RemoveChild(xnl[i]);<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; xmlDoc.Save(strTaskListPath);<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }<br /><br />3、实现结果<br /><br />&lt;?xml version="1.0" encoding="UTF-8"?&gt;<br />&lt;TestList&gt;<br /><br />&lt;/TestList&gt;<br />&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;<br />版权声明：本文为CSDN博主「春蕾夏荷_728297725」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。<br />原文链接：https://blog.csdn.net/chunleixiahe/article/details/55504152</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><span style="font-size: 18pt; font-family: 黑体, Heiti SC;"><strong><span style="color: #ff6600;">参考2</span></strong></span></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>https://www.cnblogs.com/top5/archive/2010/02/19/1669520.html</p>
<div id="topics">
<div class="post">
<h1 class="postTitle"><a id="cb_post_title_url" class="postTitle2 vertical-middle" href="https://www.cnblogs.com/top5/archive/2010/02/19/1669520.html"> C#winform 程序，代码修改app.config </a></h1>
<div class="postBody">
<div id="cnblogs_post_body" class="blogpost-body blogpost-body-html"> 用下面的方法可以操作应用程序文件夹下的配置文件： <br /> <br />在winform中使用程序读取和修改App.config里面的appSettings当中的Value值 <br /> <br />这里我写成了两个方法，以供大家参考！ <br />一，命名空间 <br />using System; <br />using System.Configuration; <br />using System.Xml; <br />二，方法 <br />//读取Value值 <br />public static string GetConfigString(string key) <br />  { <br />   // <br />   // TODO: 在此处添加构造函数逻辑 <br />   // <br />   return ConfigurationSettings.AppSettings[key]; <br />  }  <br />  //写操作 <br />  public static void SetValue(string AppKey,string AppValue) <br />  { <br />   XmlDocument xDoc = new XmlDocument(); <br />   //获取可执行文件的路径和名称 <br />   xDoc.Load(System.Windows.Forms.Application.ExecutablePath +  ".config"); <br />     <br />   XmlNode xNode; <br />   XmlElement xElem1; <br />   XmlElement xElem2; <br />   xNode =  xDoc.SelectSingleNode("//appSettings"); <br />    <br />   xElem1 = (XmlElement)xNode.SelectSingleNode("//add[@key='" +  AppKey + "']"); <br />   if ( xElem1 != null ) xElem1.SetAttribute("value",AppValue); <br />   else <br />   { <br />    xElem2 = xDoc.CreateElement("add"); <br />    xElem2.SetAttribute("key",AppKey); <br />    xElem2.SetAttribute("value",AppValue); <br />    xNode.AppendChild(xElem2); <br />   } <br />   xDoc.Save(System.Windows.Forms.Application.ExecutablePath +  ".config"); <br />
<p>  }</p>
<p>&nbsp;</p>
<p>当Properties.Settings变量的范围"scope"设置为用户"user"时，通过上述方式读写操作并不是操作
 了"test.exe.config"文件，实际操作的文件保存在"C:\Documents and  
Settings\Administrator\Local Settings\Application  
Data\"路径下面(注：Administrator是当前用户文件夹)，文件名字叫"user.config"。点击工程Properties页面 
中"设置"选项卡的"同步"按钮会提示这个路径。&nbsp;</p>



</div>
<div id="MySignature">&nbsp;</div>
<div id="blog_post_info_block">
<div id="BlogPostCategory">
    分类: 
            <a href="https://www.cnblogs.com/top5/category/183398.html" target="_blank">asp.net,C#</a></div>
<div id="EntryTag">
    标签: 
            <a href="https://www.cnblogs.com/top5/tag/winform/">winform</a>,             <a href="https://www.cnblogs.com/top5/tag/app.config/">app.config</a>,             <a href="https://www.cnblogs.com/top5/tag/%E5%AD%98%E6%94%BE%E4%BD%8D%E7%BD%AE/">存放位置</a>,             <a href="https://www.cnblogs.com/top5/tag/C%23/">C#</a></div>
<div id="blog_post_info">
<div id="green_channel">
        <a id="green_channel_digg"></a>好文要顶
        <a id="green_channel_follow"></a>关注我
    <a id="green_channel_favorite"></a>收藏该文
    <a id="green_channel_weibo" title="分享至新浪微博"></a><img src="https://common.cnblogs.com/images/icon_weibo_24.png" alt="" />
    <a id="green_channel_wechat" title="分享至微信"></a><img src="https://common.cnblogs.com/images/wechat.png" alt="" />
</div>
<div id="author_profile">
<div id="author_profile_info" class="author_profile_info">
            <a href="https://home.cnblogs.com/u/top5/" target="_blank"><img src="https://pic.cnblogs.com/face/sample_face.gif" alt="" class="author_avatar" /></a>
<div id="author_profile_detail" class="author_profile_info">
            <a href="https://home.cnblogs.com/u/top5/">与时俱进</a><br />
            <a href="https://home.cnblogs.com/u/top5/followees/">关注 - 3</a><br />
            <a href="https://home.cnblogs.com/u/top5/followers/">粉丝 - 1015</a>
        </div>



    </div>
<div id="author_profile_follow">
                <a>+加关注</a>
    </div>



</div>
<div id="div_digg">
<div class="diggit">
        <span id="digg_count" class="diggnum">0
    </span></div>
<div class="buryit">
        <span id="bury_count" class="burynum">0
    </span></div>
<div id="digg_tips" class="diggword">&nbsp;</div>



</div>




</div>
<div id="post_next_prev">

    <a class="p_n_p_prefix" href="https://www.cnblogs.com/top5/archive/2010/02/16/1668801.html">&laquo; </a> 上一篇：    <a title="发布于 2010-02-16 21:21" href="https://www.cnblogs.com/top5/archive/2010/02/16/1668801.html">C#导出Excel总结</a>
    <br />
    <a class="p_n_p_prefix" href="https://www.cnblogs.com/top5/archive/2010/02/19/1669522.html">&raquo; </a> 下一篇：    <a title="发布于 2010-02-19 22:28" href="https://www.cnblogs.com/top5/archive/2010/02/19/1669522.html">基于FMS的在线录制例子</a>

</div>



</div>



            </div>
<div class="postDesc">posted @ 
<span id="post-date">2010-02-19 22:23&nbsp;
<a href="https://www.cnblogs.com/top5/">与时俱进</a>&nbsp;
阅读(<span id="post_view_count">3176)&nbsp;
评论(<span id="post_comment_count">0)&nbsp;
<a href="https://i.cnblogs.com/EditPosts.aspx?postid=1669520" rel="nofollow">编辑</a>&nbsp;
<a>收藏</a>&nbsp;
<a>举报</a></span></span></span></div>



        </div>



	    
	    
    </div>
<p>





<a name="!comments"></a>


    <a name="commentform"></a>
    
    <span id="span_refresh_tips"></span></p>
<p>&nbsp;</p>