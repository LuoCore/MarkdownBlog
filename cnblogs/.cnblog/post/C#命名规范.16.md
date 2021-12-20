<p>https://www.cnblogs.com/kubll/p/10788171.html</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>1命名规则有两种：</p>
<p>Pascal：每个单词的首字母大写，例如ProductType</p>
<p>Camel：首个单词的首字母小写，其余单词的首字母大写，例如productType&nbsp;</p>
<div class="table-wrapper">
<table border="0" cellspacing="0">
<tbody>
<tr>
<td valign="top" width="120">
<p>标志符</p>
</td>
<td valign="top" width="74">
<p>规则</p>
</td>
<td valign="top" width="394">
<p>实例与描述</p>
</td>
</tr>
<tr>
<td valign="top" width="120">
<p>Namespace</p>
<p>命名空间</p>
</td>
<td valign="top" width="74">
<p>Pascal</p>
</td>
<td valign="top" width="394">
<p>以&ldquo;.&rdquo;分隔，当每一个限定词均为Pascal命名方式，比如：using&nbsp;ExcelQuicker.Framework</p>
</td>
</tr>
<tr>
<td valign="top" width="120">
<p>Class</p>
<p>类</p>
</td>
<td valign="top" width="74">
<p>Pascal</p>
</td>
<td valign="top" width="394">
<p>Application</p>
</td>
</tr>
<tr>
<td valign="top" width="120">
<p>Function</p>
<p>方法</p>
</td>
<td valign="top" width="74">
<p>Pascal</p>
</td>
<td valign="top" width="394">
<p>ToString</p>
</td>
</tr>
<tr>
<td valign="top" width="120">
<p>Enum</p>
<p>枚举</p>
</td>
<td valign="top" width="74">
<p>Pascal</p>
</td>
<td valign="top" width="394">
<p>Pascal命名，切勿包含Enum，否则FXCop会抛出Issue</p>
</td>
</tr>
<tr>
<td valign="top" width="120">
<p>Delegate</p>
<p>委托</p>
</td>
<td valign="top" width="74">
<p>Pascal</p>
</td>
<td valign="top" width="394">
<p>以Pascal命名，不以任何特殊字符串区别于类名、函数名，命名的后面加EventHandler</p>
</td>
</tr>
<tr>
<td valign="top" width="120">
<p>Interface</p>
<p>接口</p>
</td>
<td valign="top" width="74">
<p>Pascal</p>
</td>
<td valign="top" width="394">
<p>IDisposable&nbsp;注：总是以&nbsp;I&nbsp;前缀开始，后接Pascal命名</p>
</td>
</tr>
<tr>
<td valign="top" width="120">
<p>自定义异常类</p>
</td>
<td valign="top" width="74">
<p>&nbsp;</p>
</td>
<td valign="top" width="394">
<p>以Exception结尾</p>
</td>
</tr>
<tr>
<td valign="top" width="120">
<p>Const</p>
<p>常量</p>
</td>
<td valign="top" width="74">
<p>Pascal</p>
</td>
<td valign="top" width="394">
<p>全部大写，单词间以下划线隔开</p>
</td>
</tr>
<tr>
<td valign="top" width="120">
<p>成员变量</p>
<p>（全局变量）</p>
</td>
<td valign="top" width="74">
<p>Camel</p>
</td>
<td valign="top" width="394">
<p>加前缀<span style="font-family: Calibri;">&ldquo;_&rdquo;<span style="font-family: 宋体;">。<span style="font-family: Calibri;">&nbsp;public&nbsp;int&nbsp;_i;</span></span></span></p>
<p>&nbsp;</p>
</td>
</tr>
<tr>
<td valign="top" width="120">
<p>局部变量</p>
</td>
<td valign="top" width="74">
<p>Camel</p>
</td>
<td valign="top" width="394">
<p>首字母小写&nbsp;</p>
</td>
</tr>
<tr>
<td valign="top" width="120">
<p>数据成员</p>
</td>
<td valign="top" width="74">
<p>Camel</p>
</td>
<td valign="top" width="394">
<p>以m开头＋Pascal命名规则，如mProductType（m意味member）</p>
</td>
</tr>
<tr>
<td valign="top" width="120">
<p>string</p>
</td>
<td valign="top" width="74">
<p>Pascal</p>
</td>
<td valign="top" width="394">
<p>&nbsp;str前缀</p>
</td>
</tr>
</tbody>
</table>
</div>
<p>&nbsp;</p>
<p>2<span style="font-family: 宋体;">文件头部注释</span></p>
<p><span style="font-family: 宋体;">在代码文件的头部进行注释，这样做的好处在于，我们能对代码文件做变更跟踪。</span></p>
<p>Unity修改C#范文脚本位置：D:****\Data\Resources\ScriptTemplates</p>
<p><span style="font-family: 宋体;">样本：</span></p>
<p>/********************************************************************************</p>
<p>**&nbsp;<span style="font-family: 宋体;">作者：&nbsp;kubll</span></p>
<p>**&nbsp;<span style="font-family: 宋体;">创始时间：&nbsp;2016-2-8</span></p>
<p>**&nbsp;修改人：kubll</p>
<p>**&nbsp;修改时间：2016-3-9</p>
<p>**&nbsp;修改人：Lucy</p>
<p>**&nbsp;修改时间：2016-3-29</p>
<p>**&nbsp;描述：</p>
<p>**&nbsp;&nbsp;&nbsp;&nbsp;主要用于产品信息的资料录入，&hellip;</p>
<p>*********************************************************************************/</p>