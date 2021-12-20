<p>https://www.cnblogs.com/wanghonghu/p/4093411.html</p>
<p>&nbsp;</p>
<div class="cnblogs_code">
<pre><span style="color: rgba(0, 0, 255, 1);">set <span style="color: rgba(0, 0, 255, 1);">identity_insert 表名 <span style="color: rgba(0, 0, 255, 1);">ON <span style="color: rgba(0, 128, 128, 1);">--<span style="color: rgba(0, 128, 128, 1);">允许对自增列Id插入指定数据
<span style="color: rgba(0, 0, 255, 1);">insert <span style="color: rgba(0, 0, 255, 1);">into table_name(Id,Name) <span style="color: rgba(0, 0, 255, 1);">values(<span style="color: rgba(128, 0, 0, 1); font-weight: bold;">1,<span style="color: rgba(255, 0, 0, 1);">'<span style="color: rgba(255, 0, 0, 1);">test<span style="color: rgba(255, 0, 0, 1);">'<span style="color: rgba(0, 0, 0, 1);">)
<span style="color: rgba(0, 0, 255, 1);">set <span style="color: rgba(0, 0, 255, 1);">identity_insert 表名 <span style="color: rgba(0, 0, 255, 1);">OFF <span style="color: rgba(0, 128, 128, 1);">--<span style="color: rgba(0, 128, 128, 1);">关闭对自增列Id插入指定数据<br /></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></span></pre>
</div>
<p><br />https://www.cnblogs.com/mcgrady/p/4182486.html</p>
<p>&nbsp;</p>
<div class="cnblogs_code">
<p>-- 方法1：游标<br />-- 声明变量<br />DECLARE<br />&nbsp;&nbsp;&nbsp; @empid AS INT,<br />&nbsp;&nbsp;&nbsp; @firstname AS NVARCHAR(10),<br />&nbsp;&nbsp;&nbsp; @lastname AS NVARCHAR(20);<br />&nbsp;&nbsp; &nbsp;<br />-- 声明游标<br />DECLARE C_Employees CURSOR FAST_FORWARD FOR<br />&nbsp;&nbsp;&nbsp; SELECT empid,firstname,lastname <br />&nbsp;&nbsp;&nbsp; FROM HR.Employees<br />&nbsp;&nbsp;&nbsp; ORDER BY empid;<br />&nbsp;&nbsp; &nbsp;<br />OPEN C_Employees;<br /><br />-- 取第一条记录<br />FETCH NEXT FROM C_Employees INTO @empid,@firstname,@lastname;<br /><br />WHILE @@FETCH_STATUS=0<br />BEGIN<br />&nbsp;&nbsp;&nbsp; -- 操作<br />&nbsp;&nbsp;&nbsp; UPDATE HR.Employees SET fullname= @firstname+' '+@lastname WHERE empid=@empid;<br />&nbsp;&nbsp; &nbsp;<br />&nbsp;&nbsp;&nbsp; -- 取下一条记录<br />&nbsp;&nbsp;&nbsp; FETCH NEXT FROM C_Employees INTO @empid,@firstname,@lastname;<br />END<br /><br />-- 关闭游标<br />CLOSE C_Employees;<br /><br />-- 释放游标<br />DEALLOCATE C_Employees;</p>

</div>