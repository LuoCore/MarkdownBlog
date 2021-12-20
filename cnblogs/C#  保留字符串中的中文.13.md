<div class="cnblogs_code">
<pre> <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;summary&gt;</span>
        <span style="color: #808080;">///</span><span style="color: #008000;"> 保留中文字符串
        </span><span style="color: #808080;">///</span> <span style="color: #808080;">&lt;/summary&gt;</span>
        <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;returns&gt;&lt;/returns&gt;</span>
        <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">string</span> RetainChineseString(<span style="color: #0000ff;">this</span> <span style="color: #0000ff;">string</span><span style="color: #000000;"> str) 
        {
            StringBuilder chineseString </span>= <span style="color: #0000ff;">new</span><span style="color: #000000;"> StringBuilder();
            </span><span style="color: #0000ff;">for</span> (<span style="color: #0000ff;">int</span> i = <span style="color: #800080;">0</span>; i &lt; str.Length; i++<span style="color: #000000;">)
            {
                </span><span style="color: #0000ff;">if</span> (str[i] &gt;= <span style="color: #800080;">0x4E00</span> &amp;&amp; str[i] &lt;= <span style="color: #800080;">0x9FA5</span>) <span style="color: #008000;">//</span><span style="color: #008000;">汉字</span>
<span style="color: #000000;">                {
                    chineseString.Append(str[i]);
                }
            }
            </span><span style="color: #0000ff;">return</span> chineseString.Length&gt;<span style="color: #800080;">0</span>? chineseString.ToString():<span style="color: #0000ff;">string</span><span style="color: #000000;">.Empty;
        }</span></pre>
</div>
<p>&nbsp;</p>