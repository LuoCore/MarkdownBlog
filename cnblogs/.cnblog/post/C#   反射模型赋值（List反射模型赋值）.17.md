<div class="cnblogs_code">
<pre>   <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;summary&gt;</span>
        <span style="color: #808080;">///</span><span style="color: #008000;"> 反射模型赋值
        </span><span style="color: #808080;">///</span> <span style="color: #808080;">&lt;/summary&gt;</span>
        <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;typeparam name="T"&gt;&lt;/typeparam&gt;</span>
        <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;param name="model"&gt;&lt;/param&gt;</span>
        <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;param name="suf"&gt;&lt;/param&gt;</span>
        <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;param name="strIde"&gt;&lt;/param&gt;</span>
        <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;returns&gt;&lt;/returns&gt;</span>
        <span style="color: #0000ff;">public</span> <span style="color: #0000ff;">static</span> <span style="color: #0000ff;">void</span> ObjByPropertyInfoRecurveToT&lt;T&gt;<span style="color: #000000;">(T model)
        {
            </span><span style="color: #0000ff;">var</span> modelType =<span style="color: #000000;"> model.GetType();
            </span><span style="color: #0000ff;">var</span> enumType = modelType.GetInterface(<span style="color: #800000;">"</span><span style="color: #800000;">IEnumerable</span><span style="color: #800000;">"</span>, <span style="color: #0000ff;">false</span><span style="color: #000000;">);
            System.Reflection.PropertyInfo[] pros </span>=<span style="color: #000000;"> modelType.GetProperties();
            </span><span style="color: #0000ff;">if</span> (modelType.IsGenericType &amp;&amp; enumType != <span style="color: #0000ff;">null</span><span style="color: #000000;">)
            {
                </span><span style="color: #0000ff;">var</span> listObj = model <span style="color: #0000ff;">as</span> IEnumerable&lt;<span style="color: #0000ff;">object</span>&gt;<span style="color: #000000;">;
                </span><span style="color: #0000ff;">foreach</span> (<span style="color: #0000ff;">var</span> obj <span style="color: #0000ff;">in</span><span style="color: #000000;"> listObj)
                {
                    ObjByPropertyInfoRecurveToT(obj);
                }
            }
            </span><span style="color: #0000ff;">else</span><span style="color: #000000;"> 
            {
                </span><span style="color: #0000ff;">foreach</span> (System.Reflection.PropertyInfo pro <span style="color: #0000ff;">in</span><span style="color: #000000;"> pros) 
                {
                    </span><span style="color: #0000ff;">if</span> (pro.PropertyType.IsPrimitive ||<span style="color: #000000;"> pro.PropertyType.IsSealed)
                    {
                        </span><span style="color: #0000ff;">var</span> valueObj = pro.GetValue(model, <span style="color: #0000ff;">null</span><span style="color: #000000;">);
                    }
                    </span><span style="color: #0000ff;">else</span><span style="color: #000000;"> 
                    {
                        </span><span style="color: #0000ff;">var</span> valueObj = pro.GetValue(model, <span style="color: #0000ff;">null</span><span style="color: #000000;">);
                        ObjByPropertyInfoRecurveToT(valueObj);
                    }
                        
                }
            }

            

        }</span></pre>
</div>
<p>&nbsp;</p>