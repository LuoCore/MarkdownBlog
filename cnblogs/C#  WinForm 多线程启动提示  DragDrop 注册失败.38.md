<p>https://blog.csdn.net/educast/article/details/7954242</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>这种情况是由多线程引起的，在项目中遇到过这样的情况，查了一下网上的解决方法...汗，都不行。只有靠自己了！</p>
<p>首先在&nbsp;&nbsp;&nbsp;static void Main()&nbsp;&nbsp;函数前加上&nbsp;&nbsp;&nbsp;&nbsp; [STAThreadAttribute]&nbsp;</p>
<p>然后在新建线程的那个函数</p>
<p>&nbsp;</p>
<div style="padding-right: 5.4pt; padding-left: 5.4pt; background: #e6e6e6; padding-bottom: 4px; width: 95%; word-break: break-all; padding-top: 4px; border: windowtext 0.5pt solid;">
<div> <img src="http://images.csdn.net/syntaxhighlighting/OutliningIndicators/None.gif" alt="" align="top" /> <span style="color: #000000;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Thread&nbsp;t&nbsp; <span style="color: #000000;">= <span style="color: #000000;">&nbsp; <span style="color: #0000ff;">new <span style="color: #000000;">&nbsp;Thread( <span style="color: #0000ff;">new <span style="color: #000000;">&nbsp;ThreadStart(FlyMessage)); <span style="color: #008000;">// <span style="color: #008000;">新建了一个线程 <span style="color: #008000;"><br /> <img src="http://images.csdn.net/syntaxhighlighting/OutliningIndicators/None.gif" alt="" align="top" />
  <span style="color: #000000;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;t.ApartmentState&nbsp;
  <span style="color: #000000;">=
  <span style="color: #000000;">&nbsp;ApartmentState.STA;
  <span style="color: #008000;">//
  <span style="color: #008000;">加上这句话！ <span style="color: #008000;"><br /> <img src="http://images.csdn.net/syntaxhighlighting/OutliningIndicators/None.gif" alt="" align="top" />
  <span style="color: #000000;">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;t.Start();
  <span style="color: #008000;">//
  <span style="color: #008000;">开始线程
 </span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></div>

 
</div>