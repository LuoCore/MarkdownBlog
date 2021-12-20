<div class="info">
<h3>createWebHistory路由模式路径不带#号(生产环境下不能直接访问项目，需要nginx转发)</h3>
<blockquote>
<p>http://localhost:8080/#/</p>
</blockquote>
<pre class="brush:css;toolbar:false"><code id="mycode" class="hljs objectivec"><code><span class="hljs-keyword">const router = createRouter({  history: createWebHistory(),  routes});</span></code></code></pre>
<h3>createWebHashHistory路由模式路径带#号</h3>
<blockquote>
<p>http://localhost:8080/</p>
</blockquote>
<pre class="brush:css;toolbar:false"><code id="mycode" class="hljs objectivec"><code><span class="hljs-keyword">const router = createRouter({  history: createWebHashHistory(),  routes});</span></code></code></pre>
</div>