<div class="cnblogs_code">&nbsp;</div>
<div class="cnblogs_code">
<pre> 
<span style="color: #008000;">//</span><span style="color: #008000;">先给 DataGridView 赋值一个空表</span>
DataSet ds_temp = 数据库.getDs(<span style="color: #800000;">"</span><span style="color: #800000;">select *  from  表名 where 1=0</span><span style="color: #800000;">"</span><span style="color: #000000;">);
            </span><span style="color: #0000ff;">if</span> (ds_temp != <span style="color: #0000ff;">null</span> &amp;&amp; ds_temp.Tables.Count &gt; <span style="color: #800080;">0</span><span style="color: #000000;">)
            {
                rcomdgv1.DataSource </span>= ds_temp.Tables[<span style="color: #800080;">0</span><span style="color: #000000;">];
            }


</span><span style="color: #008000;">//</span><span style="color: #008000;">获取新增内容</span>
rcomdgv1.CurrentCell = <span style="color: #0000ff;">null</span><span style="color: #000000;">;
 </span><span style="color: #0000ff;">if</span><span style="color: #000000;"> (ds_temp.HasChanges())
{
                    </span><span style="color: #0000ff;">var</span> dsChanges =<span style="color: #000000;"> ds_temp.GetChanges();
                    </span><span style="color: #0000ff;">if</span> (dsChanges != <span style="color: #0000ff;">null</span> &amp;&amp; dsChanges.Tables.Count &lt; <span style="color: #800080;">1</span>) { <span style="color: #0000ff;">return</span><span style="color: #000000;">; }


                 
                }</span></pre>
</div>
<p>&nbsp;</p>