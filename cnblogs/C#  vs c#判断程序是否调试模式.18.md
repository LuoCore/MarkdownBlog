<p>https://blog.csdn.net/qq_37664403/article/details/118747195</p>
<p>&nbsp;</p>
<p>1.Debug模式,Release模式<br />#if DEBUG<br />Console.WriteLine(&ldquo;Debug模式&rdquo;);<br />#else<br />Console.WriteLine(&ldquo;Release模式&rdquo;);<br />#endif<br />此方法适合习惯好的程序员，但是对我来说不怎么习惯使用，因为调试个代码，和不在调试情况下运行 我不会去切换Release模式<br />&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;<br />版权声明：本文为CSDN博主「名伟」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。<br />原文链接：https://blog.csdn.net/qq_37664403/article/details/118747195</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><strong>2.vs调试模式=开发模式，发布模式=编译后直接打开软件模式</strong><br /> if (Debugger.IsAttached)<br /> {<br /> MessageBox.Show(&ldquo;调试模式已开启&rdquo;);<br /> }<br /> else<br /> {<br /> MessageBox.Show(&ldquo;发布模式已开启&rdquo;);<br /> }</p>