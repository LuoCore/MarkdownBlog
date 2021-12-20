<div class="cnblogs_code">
<pre><span style="color: #808080;">///</span> <span style="color: #808080;">&lt;summary&gt;</span>
        <span style="color: #808080;">///</span><span style="color: #008000;"> 列表项下拉窗口宽度自适应
        </span><span style="color: #808080;">///</span> <span style="color: #808080;">&lt;/summary&gt;</span>
        <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;param name="comboBox"&gt;&lt;/param&gt;</span>
        <span style="color: #0000ff;">private</span> <span style="color: #0000ff;">void</span><span style="color: #000000;"> ComboBoxAutoDropDownListWidth(ComboBox comboBox)
        {
            </span><span style="color: #0000ff;">int</span> maxWidth = <span style="color: #800080;">0</span>, temp = <span style="color: #800080;">0</span><span style="color: #000000;">;
            </span><span style="color: #0000ff;">foreach</span> (<span style="color: #0000ff;">var</span> obj <span style="color: #0000ff;">in</span><span style="color: #000000;"> comboBox.Items)
            {
                temp </span>=<span style="color: #000000;"> TextRenderer.MeasureText(comboBox.GetItemText(obj), comboBox.Font).Width;
                </span><span style="color: #0000ff;">if</span> (temp &gt;<span style="color: #000000;"> maxWidth)
                {
                    maxWidth </span>=<span style="color: #000000;"> temp;
                }
            }
            comboBox.DropDownWidth</span>= maxWidth + SystemInformation.VerticalScrollBarWidth+<span style="color: #800080;">2</span><span style="color: #000000;">;
        }</span></pre>
</div>
<p>https://www.itranslater.com/qa/details/2583418447979873280</p>