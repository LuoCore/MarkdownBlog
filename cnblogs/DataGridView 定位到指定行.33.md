<p>&nbsp;</p>
<p>https://blog.csdn.net/weixin_34198881/article/details/93301519</p>
<p>&nbsp;</p>
<div id="content_views" class="htmledit_views">
<div id="cnblogs_post_body" class="blogpost-body">
<p>//定位到指定行（样式）<br />dataGridView1.ClearSelection();<br />dataGridView1.Rows[selectIndex].Selected = true;</p>
<p>//让指定行处于选中状态（状态）<br />dataGridView1.CurrentCell = dataGridView1.Rows[selectIndex].Cells[1];<br />dataGridView1.CurrentRow.Selected = true;</p>
<p>当时使用的场景：处理行数据上移下移的情况下用的。</p>
<p>注：这四句需要放在dataGridView1.Refresh()的后面才会起作用，前面两句会定位到指定的行，后面两句会使定位到的指定行处于选中状态，若不使用后面的两句，而使用dataGridView1.CurrentRow.Index得到的index将会一直是0（第一行）</p>


</div>
<p>转载于:https://www.cnblogs.com/sugarwxx/p/9354421.html</p>
<p>&nbsp;</p>
<div class="cnblogs_Highlighter">
<pre class="brush:csharp;gutter:true;">foreach (DataGridViewRow dgvr in dataGridView2.Rows){
  this.dataGridView1.CurrentCell = dgvr.Cells["上传进度"];
this.dataGridView2.Refresh();
}
</pre>
</div>
<p>&nbsp;</p>
<p>&nbsp;</p>
</div>