<div class="cnblogs_code">
<pre> <span style="color: #008000;">//</span><span style="color: #008000;">取属性上的自定义特性给DataGridView赋值</span>
            Type objType = <span style="color: #0000ff;">typeof</span><span style="color: #000000;">(Models.Model);
            </span><span style="color: #0000ff;">foreach</span> (PropertyInfo propInfo <span style="color: #0000ff;">in</span><span style="color: #000000;"> objType.GetProperties())
            {
                </span><span style="color: #0000ff;">object</span>[] objAttrs = propInfo.GetCustomAttributes(<span style="color: #0000ff;">typeof</span>(OperationModel.AttributeClass.ModeProperty), <span style="color: #0000ff;">true</span><span style="color: #000000;">);
                </span><span style="color: #0000ff;">if</span> (objAttrs.Length &gt; <span style="color: #800080;">0</span><span style="color: #000000;">)
                {
                    OperationModel.AttributeClass.ModeProperty attr </span>= objAttrs[<span style="color: #800080;">0</span>] <span style="color: #0000ff;">as</span><span style="color: #000000;"> OperationModel.AttributeClass.ModeProperty;
                    </span><span style="color: #0000ff;">if</span> (attr != <span style="color: #0000ff;">null</span><span style="color: #000000;">)
                    {
                        </span><span style="color: #0000ff;">if</span><span style="color: #000000;"> (attr.IsVerify)
                        {
                            </span><span style="color: #0000ff;">continue</span><span style="color: #000000;">;
                        }
                        DataGridViewTextBoxColumn dgvtxtc </span>= <span style="color: #0000ff;">new</span><span style="color: #000000;"> DataGridViewTextBoxColumn();
                        dgvtxtc.Name </span>=<span style="color: #000000;"> propInfo.Name;
                        dgvtxtc.DataPropertyName </span>=<span style="color: #000000;"> propInfo.Name;
                        dgvtxtc.HeaderText </span>=<span style="color: #000000;"> attr.PropertyName;
                        </span><span style="color: #0000ff;">this</span><span style="color: #000000;">.dataGridView2.Columns.Add(dgvtxtc);
                    }
                }
            }</span></pre>
</div>
<p>&nbsp;</p>
<p>特性的写法</p>
<div class="cnblogs_code">
<pre>  <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;summary&gt;</span>
    <span style="color: #808080;">///</span><span style="color: #008000;"> 字段属性
    </span><span style="color: #808080;">///</span> <span style="color: #808080;">&lt;/summary&gt;</span>
    [AttributeUsage(AttributeTargets.Property, Inherited = <span style="color: #0000ff;">true</span><span style="color: #000000;">)]
    </span><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">class</span><span style="color: #000000;"> ModeProperty : Attribute
    {
        </span><span style="color: #0000ff;">private</span><span style="color: #000000;"> ModeProperty() { }
        </span><span style="color: #0000ff;">public</span> <span style="color: #0000ff;">string</span> PropertyName { <span style="color: #0000ff;">get</span>; <span style="color: #0000ff;">set</span><span style="color: #000000;">; }
        </span><span style="color: #0000ff;">public</span> Boolean IsNull { <span style="color: #0000ff;">get</span>; <span style="color: #0000ff;">set</span><span style="color: #000000;">; }
        </span><span style="color: #808080;">///</span> <span style="color: #808080;">&lt;summary&gt;</span>
        <span style="color: #808080;">///</span><span style="color: #008000;"> 验证字段
        </span><span style="color: #808080;">///</span> <span style="color: #808080;">&lt;/summary&gt;</span>
        <span style="color: #0000ff;">public</span> Boolean IsVerify { <span style="color: #0000ff;">get</span>; <span style="color: #0000ff;">set</span><span style="color: #000000;">; }
        </span><span style="color: #0000ff;">public</span> Boolean IsList { <span style="color: #0000ff;">get</span>; <span style="color: #0000ff;">set</span><span style="color: #000000;">; }
        </span><span style="color: #0000ff;">public</span> Type Type { <span style="color: #0000ff;">get</span>; <span style="color: #0000ff;">set</span><span style="color: #000000;">; }
        </span><span style="color: #0000ff;">public</span> ModeProperty(<span style="color: #0000ff;">string</span><span style="color: #000000;"> PropertyName)
        {
            </span><span style="color: #0000ff;">this</span>.PropertyName =<span style="color: #000000;"> PropertyName;
        }
    }</span></pre>
</div>
<p>&nbsp;</p>