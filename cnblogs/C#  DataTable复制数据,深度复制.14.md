<p>https://blog.csdn.net/fuyifang/article/details/40355025</p>
<p>&nbsp;</p>
<div class="cnblogs_code">
<pre><span style="color: #808080;">///</span> <span style="color: #808080;">&lt;summary&gt;</span>
        <span style="color: #808080;">///</span><span style="color: #008000;"> 复制数据,深度复制
        </span><span style="color: #808080;">///</span> <span style="color: #808080;">&lt;/summary&gt;</span>
        <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;param name="dataSourceRow"&gt;</span><span style="color: #008000;">数据源，待复制的数据</span><span style="color: #808080;">&lt;/param&gt;</span>
        <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;param name="dataStruct"&gt;</span><span style="color: #008000;">数据结构/表结构</span><span style="color: #808080;">&lt;/param&gt;</span>
        <span style="color: #808080;">///</span> <span style="color: #808080;">&lt;returns&gt;</span><span style="color: #008000;">处理后的DataTable</span><span style="color: #808080;">&lt;/returns&gt;</span>
        <span style="color: #0000ff;">public</span><span style="color: #000000;"> DataTable CopyData(DataTable dataStruct)
        {
            DataTable dataTable </span>= <span style="color: #0000ff;">new</span><span style="color: #000000;"> DataTable();
            </span><span style="color: #008000;">//</span><span style="color: #008000;">定义表结构</span>
<span style="color: #000000;">            DataColumn col;
            </span><span style="color: #0000ff;">foreach</span> (DataColumn column <span style="color: #0000ff;">in</span><span style="color: #000000;"> dataStruct.Columns)
            {
                col </span>= <span style="color: #0000ff;">new</span><span style="color: #000000;"> DataColumn();
                col.ColumnName </span>=<span style="color: #000000;"> column.ColumnName;
                col.DataType </span>=<span style="color: #000000;"> column.DataType;
                dataTable.Columns.Add(col);
            }
            </span><span style="color: #0000ff;">foreach</span> (DataRow row <span style="color: #0000ff;">in</span><span style="color: #000000;"> dataStruct.Rows)
            {
                DataRow tempRow </span>=<span style="color: #000000;"> dataTable.NewRow();
                </span><span style="color: #0000ff;">foreach</span> (DataColumn column <span style="color: #0000ff;">in</span><span style="color: #000000;"> dataStruct.Columns)
                {
                    </span><span style="color: #0000ff;">try</span><span style="color: #000000;">
                    {
                        tempRow[column.ColumnName] </span>=<span style="color: #000000;"> row[column.ColumnName];
                    }
                    </span><span style="color: #0000ff;">catch</span><span style="color: #000000;">
                    { </span><span style="color: #0000ff;">continue</span><span style="color: #000000;">; }
                }
                dataTable.Rows.Add(tempRow);
            }
            </span><span style="color: #0000ff;">return</span><span style="color: #000000;"> dataTable;
        }</span></pre>
</div>
<p>&nbsp;</p>