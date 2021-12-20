<p>https://www.cnblogs.com/wolfocme110/p/14727133.html</p>
<p>&nbsp;</p>
<div id="cnblogs_post_body" class="blogpost-body blogpost-body-html">
<h1><span style="font-size: 15px;">行锁使用需要注意</span></h1>
<p>1、ROWLOCK行级锁确保在用户取得被更新的行，到该行进行更新，这段时间内不被其它用户所修改。因而行级锁即可保证数据的一致性，又能提高数据操作的并发性。</p>
<p>2、ROWLOCK告诉SQL Server只使用行级锁，ROWLOCK语法可以使用在SELECT,UPDATE和DELETE语句中。</p>
<p>3、ROWLOCK指定通常采用页锁或表锁时，采用行锁。 在从 SNAPSHOT 隔离级别操作的事务中指定时，除非将 ROWLOCK 与需要锁的其他表提示（例如，UPDLOCK 和 HOLDLOCK）组合，否则不会取得行锁。</p>
<p>4、UPDLOCK指定采用更新锁并保持到事务完成。UPDLOCK 仅对行级别或页级别的读操作采用更新锁。 如果将 UPDLOCK 与 TABLOCK 组合使用或出于一些其他原因采用表级锁，将采用排他 (X) 锁。指定 UPDLOCK 时，忽略 READCOMMITTED 和 READCOMMITTEDLOCK 隔离级别提示。 例如，如果将会话的隔离级别设置为 SERIALIZABLE 且查询指定 (UPDLOCK, READCOMMITTED)，则忽略 READCOMMITTED 提示且使用 SERIALIZABLE 隔离级别运行事务。</p>
<p>5、HOLDLOCK等同于SERIALIZABLE。HOLDLOCK 仅应用于那些为其指定了 HOLDLOCK 的表或视图，并且仅在使用了 HOLDLOCK 的语句定义的事务的持续时间内应用。&nbsp;<span data-ttu-id="084da-227">HOLDLOCK 不能被用于包含 FOR BROWSE 选项的 SELECT 语句。</span></p>
<p>第一步：在当前会话中锁定数据行。</p>
<p>--声明数据库引用<br />use test;<br />go</p>
<p>--声明数据库行锁<br />begin tran tran1<br />select * from&nbsp;MPHead with(rowlock,updlock) where id=1;<br />waitfor delay '00:00:10';<br />commit tran;<br />go</p>
<p>第二步：开启新会话，进行更新锁定数据行。</p>
<p>update MPHead&nbsp;set EditBy='demo1' where id=1;</p>
<h2>示例结果：事务延迟提交十秒，在事务未提交之前进行更新会发生进程阻塞，更新是失败的，事务提交完成后行锁被释放更新才能成功。</h2>


</div>