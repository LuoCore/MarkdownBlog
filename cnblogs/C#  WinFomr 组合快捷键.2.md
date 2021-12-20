<div class="cnblogs_Highlighter">
<pre class="brush:csharp;gutter:true;"> private void 控件名称_KeyDown(object sender, KeyEventArgs e)
        {
            //如果只是按了回车，而不是按组合快捷键就执行
             if (e.KeyCode == Keys.Enter&amp;&amp;!(e.Modifiers.CompareTo(Keys.Shift) == 0 &amp;&amp; e.KeyCode == Keys.Enter))
            {
                //处理事件
            }



        }
</pre>
</div>
<p>&nbsp;</p>