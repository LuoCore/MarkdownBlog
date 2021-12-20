<div class="cnblogs_Highlighter">
<pre class="brush:sql;gutter:true;">-- =============================================
-- Author:		&lt;作者&gt;
-- Create date: &lt;时间&gt;
-- Description:	&lt;功能说明&gt;
-- =============================================
CREATE TRIGGER 触发器名称  --如果是修改用 ALTER
   ON  表名
   AFTER DELETE,INSERT,UPDATE --触发器事件
AS 
BEGIN
        --判断是那种事件被触发
	DECLARE @IsInsert bit,@IsUpdate bit,@IsDelete bit
	IF EXISTS(SELECT 1 FROM inserted) AND NOT EXISTS(SELECT 1 FROM deleted)
		SET @IsInsert = 1
	ELSE
		SET @IsInsert = 0
	IF EXISTS(SELECT 1 FROM inserted) AND EXISTS(SELECT 1 FROM deleted)
		SET @IsUpdate = 1
	ELSE
		SET @IsUpdate = 0
	IF NOT EXISTS(SELECT 1 FROM inserted) AND EXISTS(SELECT 1 FROM deleted)
		SET @IsDelete = 1
	ELSE
		SET @IsDelete = 0 





	IF @IsInsert = 1 BEGIN
		--插入事件被触发执行
             DECLARE 触发器名称 CURSOR FOR SELECT 表字段 FROM inserted;
		OPEN 触发器名称;
		FETCH NEXT FROM 触发器名称 INTO 定义赋值字段名称;
		WHILE(@@FETCH_STATUS=0) 
		BEGIN
			--要执行的动作
			FETCH NEXT FROM 触发器名称 INTO 定义赋值字段名称;
		END
		CLOSE 触发器名称;
		DEALLOCATE 触发器名称
	END
 
	IF @IsUpdate=1 BEGIN
		--修改事件被触发执行，在这里会多一个 Deleted 表，看需不需要用到
              DECLARE 触发器名称 CURSOR FOR SELECT 表字段 FROM inserted;
		OPEN 触发器名称;
		FETCH NEXT FROM 触发器名称 INTO 定义赋值字段名称;
		WHILE(@@FETCH_STATUS=0) 
		BEGIN
			--要执行的动作
			FETCH NEXT FROM 触发器名称 INTO 定义赋值字段名称;
		END
		CLOSE 触发器名称;
		DEALLOCATE 触发器名称
	END;

	IF @IsDelete = 1 BEGIN
		--删除事件被触发执行
               DECLARE 触发器名称 CURSOR FOR SELECT 表字段 FROM Deleted;
		OPEN 触发器名称;
		FETCH NEXT FROM 触发器名称 INTO 定义赋值字段名称;
		WHILE(@@FETCH_STATUS=0) 
		BEGIN
			--要执行的动作
			FETCH NEXT FROM 触发器名称 INTO 定义赋值字段名称;
		END
		CLOSE 触发器名称;
		DEALLOCATE 触发器名称
	END
END
                        
</pre>
</div>
<p>&nbsp;</p>