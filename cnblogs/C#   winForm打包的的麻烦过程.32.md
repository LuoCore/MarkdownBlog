<p>https://www.cnblogs.com/qiantao/p/9468570.html</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<div id="cnblogs_post_body" class="blogpost-body blogpost-body-html">
<p><span style="font-family: 宋体;">作为研发人员，在本机上开发的winform、wpf或者控制台程序需要发给其他人测试时候，一般需要对其进行打包生成setup安装文件，根据网上查找的资料并结合自己打包成功，记录如下：</span></p>
<p>注：本程序是一个利用winform实现的客户端程序，解决方案为</p>
<p class="p">第一步，<span style="font-family: 宋体;">右击&ldquo;解决方案XXX&rdquo;-&gt;添加&ldquo;新建项目&rdquo;-》&ldquo;其他项目类型&rdquo;-》&ldquo;安装和部署&rdquo;-》&ldquo;安装向导&rdquo;</span></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813155708726-872514801.png" alt="" class="medium-zoom-image" /></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813155938546-169247190.png" alt="" /></p>
<p class="p">&nbsp;<span style="font-family: 宋体;">然后点击下一步：</span></p>
<p class="p"><span style="font-family: 宋体;"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813160049425-1738060483.png" alt="" /></span></p>
<p class="p">&nbsp;</p>
<p class="p">&nbsp;<span style="font-family: 宋体;">这里保持默认即可&ldquo;为WIndows应用程序创建一个安装程序&rdquo;-》</span></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813171956141-1171137271.png" alt="" /></p>
<p class="p">&nbsp;<span style="font-family: 宋体;">选择&ldquo;主输出来自**（项目名称：XXX）&rdquo;<span style="font-family: 宋体;">（<span style="font-family: 宋体; background-color: rgba(255, 255, 255, 1);"><span style="color: rgba(255, 0, 0, 1);">注意：如果有多个项目合成一个解决方案也要选择，就是都选择<span style="color: rgba(255, 0, 0, 1);"><span style="font-family: 宋体;">主输出来自XXX<span style="font-family: 宋体;">）&mdash;&mdash;》</span></span></span></span></span></span></span></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813160730049-1036151209.png" alt="" /></p>
<p class="p"><span style="font-family: 宋体;">这里我们没有额外附件添加，所以直接点击下一步即可，&ldquo;完成&rdquo;即可。</span></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813160905392-1833250615.png" alt="" /></p>
<p class="p"><span style="font-family: 宋体;">到这里第一部分完成，接下来就是修改属性了。</span></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813161404092-1534886308.png" alt="" class="medium-zoom-image" /></p>
<p class="p"><span style="font-family: 宋体;">右击解决方案中的setup,选择&ldquo;属性&rdquo;-》</span></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813161544829-675053870.png" alt="" /></p>
<p class="p">第二步，<span style="font-family: 宋体;">点击&ldquo;系统必备&rdquo;-》</span></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813161704413-423750839.png" alt="" /></p>
<p class="p"><span style="font-family: 宋体;">单选按钮中，选择&ldquo;从与我的应用程序相同的位置下载系统必备组件&rdquo;-》确定</span></p>
<p><span style="font-family: 宋体;">第三步，点击，左边<img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813161844575-1892275047.png" alt="" />的&ldquo;应用程序文件夹&rdquo;-》</span></p>
<p>&nbsp;</p>
<p class="p"><span style="font-family: 宋体;">从右侧属性列表中，修改属性DefaultLocation&ldquo;[ProgramFilesFolder][Manufacturer]\[ProductName]&rdquo;为：[ProgramFilesFolder]\[ProductName]，否则安装路径不允许用户选择。</span></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p class="p"><span style="font-family: Comic Sans MS;">右击&rdquo;应用程序文件夹&ldquo;，点击&rdquo;添加&ldquo;，点击&rdquo;文件&ldquo;<span style="font-family: 宋体;">或（有文件夹）&rdquo;<span style="font-family: 宋体;">文件夹&rdquo;<span style="font-family: Comic Sans MS;">。将你的Release目录下面的文件全部<span style="font-family: 宋体;">（<span style="font-family: 宋体;">软件需要的文件夹、dll等<span style="font-family: 宋体;">）<span style="font-family: Comic Sans MS;">添加进来，有文件夹的需要在应用程序文件夹目录下新建子文件夹，同时文件夹里有文件的也需要添加进去。<span style="color: rgba(255, 0, 0, 1);"><span style="font-family: 宋体;">（<span style="font-family: 宋体;">非常重要<span style="font-family: 宋体;">）</span></span></span></span></span></span></span></span></span></span></span></span></p>
<p class="p"><span style="color: rgba(255, 0, 0, 1);"><span style="font-family: 宋体;"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813162402797-1939337781.png" alt="" /></span></span></p>
<p class="p">下图为本人添加好的：</p>
<p class="p">&nbsp;</p>
<p class="p"><span style="color: rgba(255, 0, 0, 1);"><span style="font-family: 宋体;"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813162648646-933184071.png" alt="" class="medium-zoom-image" /></span></span></p>
<p class="p">&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p class="p"><span style="font-family: 宋体;">第四步，点击&ldquo;应用程序文件夹&rdquo;，右击右边的<img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813162822841-1683186965.png" alt="" />&ldquo;主输出来自XXX(..&rdquo;创建其快捷方式（快捷方式可以改名）(注意：这里的主输出是指最终在你release版本中，程序能够产生exe运行文件的主输出)-》</span></p>
<p class="p"><span style="font-family: 宋体;">将快捷方式拖拽到&ldquo;用户的程序菜单&rdquo;和&ldquo;用户桌面&rdquo;，这样安装完成后，就会在桌面和用户的程序菜单创建相应的图标。</span></p>
<p class="p">&nbsp;<span style="font-family: 宋体;">第五步，<span style="font-family: Comic Sans MS;">创建卸载程序。右击&rdquo;应用程序文件夹&ldquo;，点击&rdquo;添加&ldquo;，选择&rdquo;文件&ldquo;，然后将"C:\Windows\System32" 下面的&rdquo;msiexec.exe&ldquo;（这个msiexec.exe文件最好选择Win7系统下的，这样可以兼容Win10系统）文件给添加进来，如果找不到，你可以直接搜。当然，你也可以再给msiexec.exe创建一个快捷方式命名为&rdquo;UnInstall&ldquo;。</span></span></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813163915933-1382910496.png" alt="" class="medium-zoom-image" /></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813163959895-1552001271.png" alt="" /></p>
<p class="p"><span style="font-family: Comic Sans MS;">命名了快捷方式之后，将Setup属性（点击解决方案里面的setup弹出属性）ProductCode拷贝到Uninstall属性的Arguments里面：</span></p>
<p class="p"><span style="font-family: Comic Sans MS;">同时在前头加上 &rdquo;/X &ldquo;，<span style="color: rgba(255, 0, 0, 1);">注意：x后面有一个空格。</span></span></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813164339471-747411333.png" alt="" /></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813164529723-1406680701.png" alt="" /></p>
<p class="p"><span style="font-family: 宋体;">第六步，添加程序图标，右键点击&ldquo;用户桌面&rdquo;中的快捷方式，然后再其属性中找到，Icon属性，浏览选取你所要添加的图标，记住，<span style="font-family: 宋体;">应该先将图标放在打包的文件夹或应用程序文件夹中，要不然无法进行指定。</span></span></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813164923827-1905824557.png" alt="" /></p>
<p class="p">&nbsp;<span style="font-family: 宋体;">第<span style="font-family: 宋体;">七步<span style="font-family: 宋体;">，右击setup项目名称，选择&ldquo;生成&rdquo;，然后到，生成的目录下拷贝出setup.exe即可安装。</span></span></span></p>
<p class="p"><span style="font-family: 宋体;">进行到第<span style="font-family: 宋体;">七<span style="font-family: 宋体;">步时，用vs<span style="font-family: 宋体;">为winform<span style="font-family: 宋体;">程序打包就已经完成了，不过此时会在安装程序的Debug<span style="font-family: 宋体;">文件夹生成2<span style="font-family: 宋体;">个文件夹、1<span style="font-family: 宋体;">个.exe<span style="font-family: 宋体;">文件和1<span style="font-family: 宋体;">个.msi<span style="font-family: 宋体;">文件，而.exe<span style="font-family: 宋体;">安装时，又依赖于.msi<span style="font-family: 宋体;">文件，另外两个文件夹是对应的&nbsp;.NET Framework&nbsp;<span style="font-family: 宋体;">组件，</span></span></span></span></span></span></span></span></span></span></span></span></span></span></p>
<p class="p"><span style="font-family: 宋体;">这个时候给客户安装时拷贝过去的内容较多，也容易安装出错，如果把这些安装内容都打在一起，形成一个.exe&nbsp;<span style="font-family: 宋体;">文件，就比较方便了，此时，可以用winrar<span style="font-family: 宋体;">的<span style="font-family: 宋体;">自解压格式压缩文件<span style="font-family: 宋体;">来实现，实现过程：</span></span></span></span></span></p>
<p class="p">1&gt;<span style="font-family: 宋体;">将要打在一起的文件及文件夹全部选中，右键&nbsp;&rarr;&ldquo;添加到压缩文件&rdquo;，在打开的压缩面板的&ldquo;常规&rdquo;选项卡中勾选&ldquo;创建自解压格式压缩文件&rdquo;，此时会发现默认的压缩文件名编程了&nbsp;&nbsp;.exe&nbsp;<span style="font-family: 宋体;">后缀名了；压缩方式最好选择&ldquo;存储&rdquo;，这样打包后的程序会很快解压缩并运行。如图：</span></span></p>
<p class="p">&nbsp;<img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813165749361-1042103407.png" alt="" class="medium-zoom-image" /></p>
<p class="p">2&gt;<span style="font-family: 宋体;">设置运行文件：再切换到&ldquo;高级&rdquo;选项卡，点击&ldquo;自解压选项&rdquo;，&ldquo;常规&rdquo;里设置程序解压后运行的文件（<span style="color: rgba(255, 0, 0, 1);">这个很重要）如图：</span></span></p>
<p class="p"><img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813170139317-1668833203.png" alt="" /></p>
<p class="p"><span style="color: rgba(0, 0, 255, 1);">&nbsp;<span style="font-family: 宋体;">或者遇到这种情况，那么提取后运行（点击安装时运行）和提取前运行（生成.exe文件时运行，将压缩成的.exe<span style="font-family: 宋体;">文件安装包的图标立马换掉，不会等到点击安装时更换）都要加上要运行的<span style="font-family: Calibri;">exe<span style="font-family: 宋体;">文件</span></span></span></span></span></p>
<p class="p">&nbsp;<img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813170303791-862359300.png" alt="" /></p>
<p class="p">3&gt;<span style="font-family: 宋体;">设置安装程序文件的图标：</span></p>
<p class="p"><span style="font-family: 宋体;">切换到&ldquo;文本和图标&rdquo;，点击&ldquo;从文件加载自解压文件图标&rdquo;后的&ldquo;浏览&rdquo;按钮，选择安装程序文件的图标，如图：</span></p>
<p class="p">&nbsp;<img src="https://images2018.cnblogs.com/blog/1405715/201808/1405715-20180813170507279-1226951424.png" alt="" /></p>
<p class="p"><span style="font-family: 宋体;">先不要着急点击&ldquo;确定&rdquo;，还有最后一项设置~ ~ ~</span></p>
<p class="p">4&gt;<span style="font-family: 宋体;">切换到&ldquo;模式&rdquo;下，勾选&ldquo;解包到临时文件夹&rdquo;和&ldquo;隐藏全部&rdquo;，再切换到&ldquo;更新&rdquo;下，勾选&ldquo;覆盖所有文件&rdquo;，一路点击&ldquo;确定&rdquo;，大功告成！！</span></p>
<p class="p"><span style="font-family: 宋体;">完成了！&nbsp;</span></p>
<p class="p">&ldquo;项目名.exe&rdquo;&nbsp;<span style="font-family: 宋体;">就是最中生成的打包文件，直接点击运行就行了！！</span></p>
<p class="p"><span style="font-family: 宋体;">以上就是本人结合网上资料和其他博友文章，亲身实践成功的C# Winform程序打包成安装项目的心得，并且里面还加入了本人碰到的一些注意事项，特地写成文章分享给大家。</span></p>
</div>