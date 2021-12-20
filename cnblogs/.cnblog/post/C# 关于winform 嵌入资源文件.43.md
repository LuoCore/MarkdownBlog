<p>https://blog.csdn.net/yl2isoft/article/details/16918311</p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p><strong>None</strong>: 此文件不参与编译也不被输出。比如：工程中的文档文件, readme.txt。</p>
<p>* <strong>Compile</strong>: 参与编译并输出。主要是代码文件。</p>
<p>* <strong>Content</strong>： 不参与编译，但会被输出。</p>
<p>* <strong>Embedded Resource</strong>： 此文件被嵌入到主工程生成的DLL或exe中。主要是资源文件。</p>
<p>* <strong>ApplicationDefinition</strong>: 和Page类似，但只用于Silverlight的启动页面（默认是App.xaml)。</p>
<p>* <strong>Page</strong>: Silverligh中所有的usercontrol/page/childwindow xaml都属于"Page&rdquo; build，其它的build action不能将code behind文件和xaml文件连接起来。</p>