<div class="cnblogs_Highlighter">
<pre class="brush:sql;gutter:true;">SELECT *
FROM Billcode_in a
     LEFT JOIN Billcode_place b ON a.billcode=b.billcode AND b.id=(SELECT MAX(id)
                                                                   FROM Billcode_place
                                                                   WHERE billcode=b.billcode AND place_wavehouse_id=5);
</pre>
</div>
<p>&nbsp;</p>