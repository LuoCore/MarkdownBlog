<p><a href="https://www.cxyzjd.com/article/q913777031/118439760">SQLite Encryption(加密)问题_码农01号的博客-程序员宅基地 - 程序员宅基地 (cxyzjd.com)</a></p>
<p><a href="https://www.cxyzjd.com/article/q913777031/118439760">SQLite Encryption(加密)问题_码农01号的博客-程序员宅基地 - 程序员宅基地 (cxyzjd.com)</a></p>
<p>&nbsp;</p>
<h2>SQLite Encryption(加密)问题_码农01号的博客-程序员宅基地</h2>
<p>技术标签：&nbsp;<a title="C#" href="https://www.cxyzjd.com/searchArticle?qc=C#&amp;page=1">C#</a>&nbsp;&nbsp;<a title="sqlite" href="https://www.cxyzjd.com/searchArticle?qc=sqlite&amp;page=1">sqlite</a>&nbsp;&nbsp;<a title="SQLite" href="https://www.cxyzjd.com/searchArticle?qc=SQLite&amp;page=1">SQLite</a>&nbsp;&nbsp;</p>
<div id="article_content">
<div id="content_views" class="markdown_views prism-atom-one-dark">
<h3>什么是SQLite?</h3>
<p>SQLite是一个C语言实现的小型、快速、自包含、高可靠性、功能全面的SQL数据库引擎。</p>
<p><strong>起因：</strong><br />刚好项目上有个需求，需要使用VS2019+.Net famework 4.6.1+sqlite完成数据层。</p>
<h3>System.Data.SQLite库</h3>
<p>先尝试了官方的<a href="https://system.data.sqlite.org/index.html/doc/trunk/www/index.wiki">System.Data.SQLite</a>&nbsp;包。</p>
<p><strong>首先，使用VS2019创建.名字为 TestSqlite的.Net famework 4.6.1的控制台项目。</strong></p>
<p><strong>通过nuget安装</strong><br /><img src="https://img-blog.csdnimg.cn/20210703172709102.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3E5MTM3NzcwMzE=,size_16,color_FFFFFF,t_70" alt="![(https://img-blog.csdnimg.cn/20210703172632243.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3E5MTM3NzcwMzE=,size_16,color_FFFFFF,t_70)" /></p>
<p>这个库依赖了很多如linq、EF6等其他库.个人不是很喜欢&middot;&middot;&middot;有需要的朋友直接安装是可以的。</p>
<h3>Stub.System.Data.SQLite.Core.NetFramework</h3>
<p>这个库没有依赖项&middot;&middot;&middot;这里推荐&middot;&middot;&middot;<br /><img src="https://img-blog.csdnimg.cn/20210703172848713.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3E5MTM3NzcwMzE=,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述" /></p>
<p>通过nuget安装后使用如下代码成功运行。</p>
<pre><code class="prism language-csharp"><span class="token keyword">using System<span class="token punctuation">;
<span class="token keyword">using System<span class="token punctuation">.Data<span class="token punctuation">.SQLite<span class="token punctuation">;

<span class="token keyword">namespace TestSqlite
<span class="token punctuation">{
    
    <span class="token keyword">internal <span class="token keyword">class <span class="token class-name">Program
    <span class="token punctuation">{
    
        <span class="token keyword">private <span class="token keyword">static <span class="token keyword">void <span class="token function">Main<span class="token punctuation">(<span class="token keyword">string<span class="token punctuation">[<span class="token punctuation">] args<span class="token punctuation">)
        <span class="token punctuation">{
    
            <span class="token keyword">string cs <span class="token operator">= <span class="token string">"Data Source=TestSqlite.sqlite"<span class="token punctuation">;<span class="token comment">//数据库连接字符串
            <span class="token keyword">string stm <span class="token operator">= <span class="token string">"SELECT SQLITE_VERSION()"<span class="token punctuation">;<span class="token comment">//查看版本
            <span class="token keyword">var con <span class="token operator">= <span class="token keyword">new <span class="token class-name">SQLiteConnection<span class="token punctuation">(cs<span class="token punctuation">)<span class="token punctuation">;<span class="token comment">//创建连接
            con<span class="token punctuation">.<span class="token function">Open<span class="token punctuation">(<span class="token punctuation">)<span class="token punctuation">;
            <span class="token keyword">var cmd <span class="token operator">= <span class="token keyword">new <span class="token class-name">SQLiteCommand<span class="token punctuation">(stm<span class="token punctuation">, con<span class="token punctuation">)<span class="token punctuation">;
            <span class="token keyword">string version <span class="token operator">= cmd<span class="token punctuation">.<span class="token function">ExecuteScalar<span class="token punctuation">(<span class="token punctuation">)
                <span class="token punctuation">.<span class="token function">ToString<span class="token punctuation">(<span class="token punctuation">)<span class="token punctuation">;<span class="token comment">//查看版本
            Console<span class="token punctuation">.<span class="token function">WriteLine<span class="token punctuation">($<span class="token string">"SQLite version: {version}"<span class="token punctuation">)<span class="token punctuation">;
            Console<span class="token punctuation">.<span class="token function">ReadKey<span class="token punctuation">(<span class="token punctuation">)<span class="token punctuation">;
        <span class="token punctuation">}
    <span class="token punctuation">}
<span class="token punctuation">}
</span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></pre>
<p>运行后成功，可以看到版本是3.35.5<br /><img src="https://img-blog.csdnimg.cn/20210703173148606.png" alt="在这里插入图片描述" /><br />在bin文件夹下也生成了sqlite数据库<br /><img src="https://img-blog.csdnimg.cn/20210703173304573.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3E5MTM3NzcwMzE=,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述" /></p>
<h3>加密失败</h3>
<p>作为一个数据库，没有密码是不行的。<br />于是我们在连接字符串加上password<br /><img src="https://img-blog.csdnimg.cn/20210703173621610.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3E5MTM3NzcwMzE=,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述" /><br />运行，报错</p>
<blockquote>
<p><strong>System.IO.FileNotFoundException:&ldquo;未能加载文件或程序集&ldquo;System.Data.SQLite.SEE.License, Version=1.0.114.0, Culture=neutral, PublicKeyToken=433d9874d0bb98c5&rdquo;或它的某一个依赖项。系统找不到指定的文件</strong>。&rdquo;</p>

</blockquote>
<p><img src="https://img-blog.csdnimg.cn/20210703173658148.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3E5MTM3NzcwMzE=,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述" /><br />这个<code>System.Data.SQLite.SEE(SQLite Encryption Extension)</code>&nbsp;是System.Data.SQLite 的官方 SQLite 加密扩展包。</p>
<p>没错&middot;&middot;&middot;SQlite开源版本是加密收费的&middot;&middot;&middot;购买需要<strong>2000</strong>$&middot;&middot;&middot;&middot;&middot;<br /><img src="https://img-blog.csdnimg.cn/20210703174902289.png" alt="在这里插入图片描述" /></p>
<blockquote>
<p>贫穷让我另谋出路</p>

</blockquote>
<h3>曲线救国 ：Microsoft.Data.Sqlite</h3>
<p>经过资料查询，发现微软的<code>Microsoft.Data.Sqlite</code>&nbsp;库支持，所以再次进行尝试。</p>
<p>首先，使用VS2019创建.名字为 TestSqlite的.Net famework 4.6的控制台项目。</p>
<p><strong>通过NuGet安装 Microsoft.Data.Sqlite.Core和 SQLitePCLRaw.bundle_e_sqlcipher</strong><br /><img src="https://img-blog.csdnimg.cn/20210705162215468.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3E5MTM3NzcwMzE=,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述" /><br /><img src="https://img-blog.csdnimg.cn/20210705162230843.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3E5MTM3NzcwMzE=,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述" /></p>
<p><strong>或</strong>通过程序包管理器安装</p>
<p><code>Install-Package Microsoft.Data.Sqlite.Core</code><br />另外我们需要安装加密包<br /><code>Install-Package SQLitePCLRaw.bundle_e_sqlcipher</code>&middot;</p>
<p><strong>Dapper.Crud</strong></p>
<p>个人比较喜欢Dapper,不喜欢的小伙伴可以使用自己的ORM，不用安装这个，使用自己喜欢的方式创建表即可。</p>
<pre><code class="prism language-csharp">Install<span class="token operator">-<span class="token class-name">Package Dapper<span class="token punctuation">.Crud
</span></span></span></code></pre>
<p>安装完成后使用如下代码</p>
<pre><code class="prism language-csharp"><span class="token keyword">using System<span class="token punctuation">;
<span class="token keyword">using System<span class="token punctuation">.Data<span class="token punctuation">;
<span class="token keyword">using Dapper<span class="token punctuation">;
<span class="token keyword">using Microsoft<span class="token punctuation">.Data<span class="token punctuation">.Sqlite<span class="token punctuation">;
<span class="token keyword">namespace TestSqlite
<span class="token punctuation">{
    
    <span class="token keyword">internal <span class="token keyword">class <span class="token class-name">Program
    <span class="token punctuation">{
    
        
        <span class="token keyword">private <span class="token keyword">static <span class="token keyword">void <span class="token function">Main<span class="token punctuation">(<span class="token keyword">string<span class="token punctuation">[<span class="token punctuation">] args<span class="token punctuation">)
        <span class="token punctuation">{
    

          <span class="token keyword">var connStr <span class="token operator">= <span class="token string">@"Data Source=TestSqlite.sqlite;"<span class="token punctuation">;<span class="token comment">//连接字符串

          <span class="token keyword">var conn <span class="token operator">= <span class="token keyword">new <span class="token class-name">SqliteConnectionStringBuilder<span class="token punctuation">(connStr<span class="token punctuation">)
            <span class="token punctuation">{
    
                Mode <span class="token operator">= SqliteOpenMode<span class="token punctuation">.ReadWriteCreate<span class="token punctuation">,
                Password <span class="token operator">= <span class="token string">"password"
            <span class="token punctuation">}<span class="token punctuation">.<span class="token function">ToString<span class="token punctuation">(<span class="token punctuation">)<span class="token punctuation">;<span class="token comment">//使用这个方式设置密码，避免sql注入

            <span class="token keyword">var connection <span class="token operator">= <span class="token keyword">new <span class="token class-name">SqliteConnection<span class="token punctuation">(conn<span class="token punctuation">)<span class="token punctuation">;<span class="token comment">//创建SQLite连接
            <span class="token keyword">if <span class="token punctuation">(connection<span class="token punctuation">.State <span class="token operator">== ConnectionState<span class="token punctuation">.Closed<span class="token punctuation">)
            <span class="token punctuation">{
    
       
                connection<span class="token punctuation">.<span class="token function">Open<span class="token punctuation">(<span class="token punctuation">)<span class="token punctuation">;
                <span class="token keyword">var createTableSqlStr <span class="token operator">= <span class="token string">@"CREATE TABLE  if not exists ""Alarm"" ( ""Id"" INTEGER NOT NULL, ""AlarmName"" TEXT, ""AlarmTypeId"" INTEGER, PRIMARY KEY ( ""Id"" ) );"<span class="token punctuation">;
                <span class="token keyword">var result <span class="token operator">= connection<span class="token punctuation">.<span class="token function">Execute<span class="token punctuation">(createTableSqlStr<span class="token punctuation">)<span class="token punctuation">;<span class="token comment">//使用Dapper执行sql语句创建表
                Console<span class="token punctuation">.<span class="token function">ReadKey<span class="token punctuation">(<span class="token punctuation">)<span class="token punctuation">;
            <span class="token punctuation">}

         
        <span class="token punctuation">}

        
    <span class="token punctuation">}
<span class="token punctuation">}
</span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></code></pre>
<p>运行后成功！<br /><img src="https://img-blog.csdnimg.cn/20210703180405217.png" alt="在这里插入图片描述" /><br />这里有个需要注意的点:</p>
<blockquote>
<p><strong>在设置密码创建数据库后，需要使用ORM执行sql创建表，如果是空数据库，是未加密的&middot;&middot;可以直接打开。原因暂未可知。希望知道的大佬能告知</strong></p>

</blockquote>
<p>我们使用Navicat for SQLite 打开，如果出现以下弹窗，就说明加密成功了！<br /><img src="https://img-blog.csdnimg.cn/20210705163849571.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3E5MTM3NzcwMzE=,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述" /></p>
<h3>使用Navicat for SQLite 打开加密数据库</h3>
<p>没有Navicat的童鞋点<a href="http://www.ddooo.com/softdown/163984.htm">这里下载安装</a></p>
<h4>替换sqlite3.dll</h4>
<p>步骤如下：<br />打开Bin文件夹下的runtimes</p>
<p class=" aBigClassNameToAvoidCollisionInText aBigClassNameToAvoidCollisionInText"><img src="https://img-blog.csdnimg.cn/20210705165145965.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3E5MTM3NzcwMzE=,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述" /><br /><strong>根据自己系统选择文件夹x64还是x86</strong><br />复制win-x64\native 下的e_sqlcipher.dll<br /><img src="https://img-blog.csdnimg.cn/20210705165305405.png" alt="在这里插入图片描述" /><br />打开Navicat 的安装目录，将刚刚复制的e_sqlcipher.dll复制到该目录下。<br />备份sqlite3.dll(将该dll复制到其他文件夹下)，<br /><strong>然后将复制的e_sqlcipher.dll改名成 sqlite3.dll 替换掉原来的sqlite3.dll</strong></p>
<h4>设置密码</h4>
<p>在数据库连接右键编辑连接&ndash;&gt;高级&ndash;&gt;设置数据库文件位置&ndash;&gt;勾选已加密&ndash;&gt;设置密码&ndash;&gt;勾选保存密码<br /><img src="https://img-blog.csdnimg.cn/20210705165842615.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3E5MTM3NzcwMzE=,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述" /><br /><strong>双击连接数据库，连接成功！！</strong><br /><img src="https://img-blog.csdnimg.cn/20210705170110154.png" alt="在这里插入图片描述" /></p>

</div>

</div>
<div>
<div class="article-copyright"><span class="creativecommons"><span class="creativecommons">版权声明：本文为博主原创文章，遵循<a href="https://creativecommons.org/licenses/by-sa/4.0/" rel="noopener" target="_blank">&nbsp;CC 4.0 BY-SA&nbsp;</a>版权协议，转载请附上原文出处链接和本声明。</span></span>
<div class="article-source-link2222">本文链接：<a href="https://blog.csdn.net/q913777031/article/details/118439760">https://blog.csdn.net/q913777031/article/details/118439760</a></div>

</div>

</div>