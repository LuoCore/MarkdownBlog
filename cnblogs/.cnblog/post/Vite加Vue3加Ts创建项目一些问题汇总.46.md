<p>版权声明：本文为CSDN博主「一尾流莺_」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。<br />原文链接：https://blog.csdn.net/m0_48721669/article/details/115732258</p>
<p>&nbsp;</p>
<p>在&nbsp;vite.config.ts 中添加导入路径设置别名，显示没有导入包&nbsp;</p>
<div>import&nbsp;path&nbsp;from&nbsp;'path'</div>
<div>&nbsp;</div>
<div>需要先安装一下<code>typescript</code>的类型声明文件</div>
<div>npm add @types<span class="token operator">/node <span class="token operator">-<span class="token constant">D</span></span></span></div>
<p>然后就没有错误提示了，你可以快乐的设置别名了</p>
<div>
<div>//&nbsp;https://vitejs.dev/config/</div>
<div>export&nbsp;default&nbsp;defineConfig({</div>
<div>&nbsp;&nbsp;&nbsp;//定义别名</div>
<div>&nbsp;&nbsp;&nbsp;alias:&nbsp;{</div>
<div>&nbsp;&nbsp;&nbsp;&nbsp;"@":&nbsp;path.resolve(__dirname,&nbsp;"src"),</div>
<div>&nbsp;&nbsp;&nbsp;&nbsp;coms:&nbsp;path.resolve(__dirname,&nbsp;"src/components"),</div>
<div>&nbsp;&nbsp;},</div>
<div>&nbsp;&nbsp;//通过插件形式挂载vue</div>
<div>&nbsp;&nbsp;plugins:&nbsp;[vue()]</div>
<div>})</div>
<div>&nbsp;</div>
<div>
<p>但是我们在vscode中敲代码的时候并没有路径提示,这个时候我们再来修改一下tsconfig.json文件,在compilerOptions这个配置项下添加如下代码</p>
<p> "compilerOptions": {<br />    "baseUrl":".",<br />    "paths": {<br />      "@/*":["src/*"],<br />      "coms/*":["src/components/*"]<br />    }<br />  },</p>
<div class="cnblogs_Highlighter">
<pre class="brush:javascript;gutter:true;">{
  "compilerOptions": {
    "target": "esnext",
    "module": "esnext",
    "moduleResolution": "node",
    "strict": true,
    "jsx": "preserve",
    "sourceMap": true,
    "resolveJsonModule": true,
    "esModuleInterop": true,
    "lib": ["esnext", "dom"],
    "baseUrl":".",
    "paths": {
        "@/*":["src/*"],
        "coms/*":["src/components/*"]
    }
  },
  "include": ["src/**/*.ts", "src/**/*.d.ts", "src/**/*.tsx", "src/**/*.vue"]
}
</pre>
</div>
<p>　　再去App.vue 中修改</p>
<div>import&nbsp;HelloWorld&nbsp;from&nbsp;'./components/HelloWorld.vue'</div>
<div>为</div>
<div>
<div>import&nbsp;HelloWorld&nbsp;from&nbsp;'coms/HelloWorld.vue'</div>
<div>&nbsp;</div>
<div>
<p>我们通过配置<code>alias</code>来定义路径的别名,配置完以后我们打开<code>App.vue</code><br />把<code>HelloWorld</code>组件的引用由<code>./components/HelloWorld.vue</code>改为<code>coms/HelloWorld.vue</code></p>
<p>页面正常显示,我们的&nbsp;路径别名&nbsp;就配置成功了</p>


</div>


</div>
<p><br />&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;&mdash;<br />https://www.cnblogs.com/ainyi/p/13927377.html</p>
<p>在 src 下新建 router 文件夹，并在文件夹内创建 index.ts</p>
<p>&nbsp;</p>
<div class="cnblogs_code">
<pre>import { createRouter, createWebHistory } from 'vue-router'  <span style="color: #000000;">

const routes </span>=<span style="color: #000000;"> [
  {
    path: </span>'/'<span style="color: #000000;">,
    name: </span>'Home'<span style="color: #000000;">,
    component: () </span>=&gt; import('/@/views/Home.vue'<span style="color: #000000;">)
  },
  {
    path: </span>'/lifeCycle'<span style="color: #000000;">,
    name: </span>'lifeCycle'<span style="color: #000000;">,
    component: () </span>=&gt; import('/@/views/LifeCycle.vue'<span style="color: #000000;">)
  }
]

export </span><span style="color: #0000ff;">default</span><span style="color: #000000;"> createRouter({
  history: createWebHistory(</span>'/krry/'<span style="color: #000000;">),
  routes
})</span></pre>
</div>
<pre>import { createRouter, createWebHistory } from 'vue-router'   显示没有导入这个包，或找不到 vue-router 模块</pre>
<p><span class="hljs-keyword">&nbsp;运行：npm add vue-router@next -D</span></p>
<p>&nbsp;</p>
<p>&nbsp;</p>
<p>一般项目结构</p>
<div class="cnblogs_code">
<pre>├── publish/<span style="color: #000000;">
└── src</span>/<span style="color: #000000;">
    ├── assets</span>/                    <span style="color: #008000;">//</span><span style="color: #008000;"> 静态资源目录</span>
    ├── components/                <span style="color: #008000;">//</span><span style="color: #008000;"> 公共组件目录</span>
    ├── layout/                    <span style="color: #008000;">//</span><span style="color: #008000;"> 项目布局目录</span>
    ├── router/                    <span style="color: #008000;">//</span><span style="color: #008000;"> 路由配置目录</span>
    ├── store/                     <span style="color: #008000;">//</span><span style="color: #008000;"> 状态管理目录</span>
    ├── styles/                    <span style="color: #008000;">//</span><span style="color: #008000;"> 通用样式目录</span>
    ├── utils/                     <span style="color: #008000;">//</span><span style="color: #008000;"> 工具函数目录</span>
    ├── views/                     <span style="color: #008000;">//</span><span style="color: #008000;"> 页面组件目录</span>
<span style="color: #000000;">    ├── App.vue
    ├── main.js
├── index.html
├── vite.config.js                 </span><span style="color: #008000;">//</span><span style="color: #008000;"> Vite 配置文件</span>
└── package.json</pre>
</div>
<p>&nbsp;</p>
</div>
<div>&nbsp;</div>
<div>&nbsp;</div>
</div>