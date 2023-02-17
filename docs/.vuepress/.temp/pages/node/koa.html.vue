<template><div><h1 id="koa" tabindex="-1"><a class="header-anchor" href="#koa" aria-hidden="true">#</a> koa</h1>
<h2 id="安装" tabindex="-1"><a class="header-anchor" href="#安装" aria-hidden="true">#</a> 安装</h2>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>npm install koa
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><code v-pre>https://github.com/koajs/koa</code></p>
<h2 id="初体验hello-koa" tabindex="-1"><a class="header-anchor" href="#初体验hello-koa" aria-hidden="true">#</a> 初体验Hello koa</h2>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">const</span> Koa <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">"koa"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">const</span> app <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Koa</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token comment">// response</span>
app<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token parameter">ctx</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
    ctx<span class="token punctuation">.</span>body <span class="token operator">=</span> <span class="token string">"Hello Koa"</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token function">listen</span><span class="token punctuation">(</span><span class="token number">8000</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
    console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"koa初体验服务器启动成功~"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h2 id="中间件" tabindex="-1"><a class="header-anchor" href="#中间件" aria-hidden="true">#</a> 中间件</h2>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">const</span> Koa <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> app <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Koa</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token comment">// use注册中间件</span>
app<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token parameter">ctx<span class="token punctuation">,</span> next</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  <span class="token keyword">if</span> <span class="token punctuation">(</span>ctx<span class="token punctuation">.</span>request<span class="token punctuation">.</span>url <span class="token operator">===</span> <span class="token string">'/login'</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span>ctx<span class="token punctuation">.</span>request<span class="token punctuation">.</span>method <span class="token operator">===</span> <span class="token string">'GET'</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
      console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"来到了这里~"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
      ctx<span class="token punctuation">.</span>response<span class="token punctuation">.</span>body <span class="token operator">=</span> <span class="token string">"Login Success~"</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
  <span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token punctuation">{</span>
    ctx<span class="token punctuation">.</span>response<span class="token punctuation">.</span>body <span class="token operator">=</span> <span class="token string">"other request~"</span><span class="token punctuation">;</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token comment">// 没有提供下面的注册方式</span>
<span class="token comment">// methods方式: app.get()/.post</span>
<span class="token comment">// path方式: app.use('/home', (ctx, next) => {})</span>
<span class="token comment">// 连续注册: app.use((ctx, next) => {</span>
<span class="token comment">// }, (ctx, next) => {</span>
<span class="token comment">// })</span>

app<span class="token punctuation">.</span><span class="token function">listen</span><span class="token punctuation">(</span><span class="token number">8000</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"koa初体验服务器启动成功~"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h2 id="路由" tabindex="-1"><a class="header-anchor" href="#路由" aria-hidden="true">#</a> 路由</h2>
<p>依赖<code v-pre>koa-router</code></p>
<p>安装</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>npm install koa-router
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>router.js</p>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">const</span> Router <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa-router'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> router <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Router</span><span class="token punctuation">(</span><span class="token punctuation">{</span><span class="token literal-property property">prefix</span><span class="token operator">:</span> <span class="token string">"/users"</span><span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

router<span class="token punctuation">.</span><span class="token function">get</span><span class="token punctuation">(</span><span class="token string">'/'</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token parameter">ctx<span class="token punctuation">,</span> next</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  ctx<span class="token punctuation">.</span>response<span class="token punctuation">.</span>body <span class="token operator">=</span> <span class="token string">"User Lists~"</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

router<span class="token punctuation">.</span><span class="token function">put</span><span class="token punctuation">(</span><span class="token string">'/'</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token parameter">ctx<span class="token punctuation">,</span> next</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  ctx<span class="token punctuation">.</span>response<span class="token punctuation">.</span>body <span class="token operator">=</span> <span class="token string">"put request~"</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>


module<span class="token punctuation">.</span>exports <span class="token operator">=</span> router<span class="token punctuation">;</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>使用</p>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">const</span> Koa <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> userRouter <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'./router/user'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> app <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Koa</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token parameter">ctx<span class="token punctuation">,</span> next</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  <span class="token comment">// ctx.response.body = "Hello World";</span>
  <span class="token function">next</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span>userRouter<span class="token punctuation">.</span><span class="token function">routes</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
app<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span>userRouter<span class="token punctuation">.</span><span class="token function">allowedMethods</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token function">listen</span><span class="token punctuation">(</span><span class="token number">8000</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"koa路由服务器启动成功~"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h2 id="参数解析-query-params" tabindex="-1"><a class="header-anchor" href="#参数解析-query-params" aria-hidden="true">#</a> 参数解析-query-params</h2>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">const</span> Koa <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> app <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Koa</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">const</span> Router <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa-router'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> userRouter <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Router</span><span class="token punctuation">(</span><span class="token punctuation">{</span><span class="token literal-property property">prefix</span><span class="token operator">:</span> <span class="token string">'/users'</span><span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

userRouter<span class="token punctuation">.</span><span class="token function">get</span><span class="token punctuation">(</span><span class="token string">'/:id'</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token parameter">ctx<span class="token punctuation">,</span> next</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span>ctx<span class="token punctuation">.</span>request<span class="token punctuation">.</span>params<span class="token punctuation">)</span><span class="token punctuation">;</span>
  console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span>ctx<span class="token punctuation">.</span>request<span class="token punctuation">.</span>query<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span>

<span class="token comment">// app.use((ctx, next) => {</span>
<span class="token comment">//   console.log(ctx.request.url);</span>
<span class="token comment">//   console.log(ctx.request.query);</span>
<span class="token comment">//   console.log(ctx.request.params);</span>
<span class="token comment">//   ctx.response.body = "Hello World";</span>
<span class="token comment">// });</span>

app<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span>userRouter<span class="token punctuation">.</span><span class="token function">routes</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token function">listen</span><span class="token punctuation">(</span><span class="token number">8000</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"参数处理服务器启动成功~"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h2 id="参数解析-json-urlencoded-formdata" tabindex="-1"><a class="header-anchor" href="#参数解析-json-urlencoded-formdata" aria-hidden="true">#</a> 参数解析-json-urlencoded-formdata</h2>
<p>依赖<code v-pre>koa-bodyparser</code></p>
<p>安装</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>npm install koa-bodyparser
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">const</span> Koa <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">const</span> bodyParser <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa-bodyparser'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>


<span class="token keyword">const</span> app <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Koa</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>



app<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span><span class="token function">bodyParser</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>


app<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token parameter">ctx<span class="token punctuation">,</span> next</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span>ctx<span class="token punctuation">.</span>request<span class="token punctuation">.</span>body<span class="token punctuation">)</span><span class="token punctuation">;</span>
  console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span>ctx<span class="token punctuation">.</span>req<span class="token punctuation">.</span>body<span class="token punctuation">)</span><span class="token punctuation">;</span>
  ctx<span class="token punctuation">.</span>response<span class="token punctuation">.</span>body <span class="token operator">=</span> <span class="token string">"Hello World"</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token function">listen</span><span class="token punctuation">(</span><span class="token number">8000</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"koa初体验服务器启动成功~"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h2 id="文件上传" tabindex="-1"><a class="header-anchor" href="#文件上传" aria-hidden="true">#</a> 文件上传</h2>
<p>依赖<code v-pre>koa-multer</code></p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>npm install koa-multer
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">const</span> Koa <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">const</span> Router <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa-router'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">const</span> multer <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa-multer'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> app <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Koa</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">const</span> uploadRouter <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Router</span><span class="token punctuation">(</span><span class="token punctuation">{</span><span class="token literal-property property">prefix</span><span class="token operator">:</span> <span class="token string">'/upload'</span><span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token comment">// const storage = multer.diskStorage({</span>
<span class="token comment">//   destination,</span>
<span class="token comment">//   filename,</span>
<span class="token comment">// })</span>

<span class="token keyword">const</span> upload <span class="token operator">=</span> <span class="token function">multer</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
  <span class="token literal-property property">dest</span><span class="token operator">:</span> <span class="token string">'./uploads/'</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

uploadRouter<span class="token punctuation">.</span><span class="token function">post</span><span class="token punctuation">(</span><span class="token string">'/avatar'</span><span class="token punctuation">,</span> upload<span class="token punctuation">.</span><span class="token function">single</span><span class="token punctuation">(</span><span class="token string">'avatar'</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token parameter">ctx<span class="token punctuation">,</span> next</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span>ctx<span class="token punctuation">.</span>req<span class="token punctuation">.</span>file<span class="token punctuation">)</span><span class="token punctuation">;</span>
  ctx<span class="token punctuation">.</span>response<span class="token punctuation">.</span>body <span class="token operator">=</span> <span class="token string">"上传头像成功~"</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span>uploadRouter<span class="token punctuation">.</span><span class="token function">routes</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token function">listen</span><span class="token punctuation">(</span><span class="token number">8000</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"koa初体验服务器启动成功~"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h2 id="响应内容" tabindex="-1"><a class="header-anchor" href="#响应内容" aria-hidden="true">#</a> 响应内容</h2>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">const</span> Koa <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> app <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Koa</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token parameter">ctx<span class="token punctuation">,</span> next</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  <span class="token comment">// ctx.request.query</span>
  <span class="token comment">// ctx.query</span>

  <span class="token comment">// 设置内容</span>
  <span class="token comment">// ctx.response.body</span>
  <span class="token comment">// ctx.response.body = "Hello world~"</span>
  <span class="token comment">// ctx.response.body = {</span>
  <span class="token comment">//   name: "coderwhy",</span>
  <span class="token comment">//   age: 18,</span>
  <span class="token comment">//   avatar_url: "https://abc.png"</span>
  <span class="token comment">// };</span>
  <span class="token comment">// 设置状态码</span>
  <span class="token comment">// ctx.response.status = 400;</span>
  <span class="token comment">// ctx.response.body = ["abc", "cba", "nba"];</span>

  <span class="token comment">// ctx.response.body = "Hello World~";</span>
  ctx<span class="token punctuation">.</span>status <span class="token operator">=</span> <span class="token number">404</span><span class="token punctuation">;</span>
  ctx<span class="token punctuation">.</span>body <span class="token operator">=</span> <span class="token string">"Hello Koa~"</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token function">listen</span><span class="token punctuation">(</span><span class="token number">8000</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"koa初体验服务器启动成功~"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h2 id="静态服务器" tabindex="-1"><a class="header-anchor" href="#静态服务器" aria-hidden="true">#</a> 静态服务器</h2>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">const</span> Koa <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">const</span> staticAssets <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'koa-static'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> app <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">Koa</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span><span class="token function">staticAssets</span><span class="token punctuation">(</span><span class="token string">'./build'</span><span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

app<span class="token punctuation">.</span><span class="token function">listen</span><span class="token punctuation">(</span><span class="token number">8000</span><span class="token punctuation">,</span> <span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
  console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"koa初体验服务器启动成功~"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h2 id="部署" tabindex="-1"><a class="header-anchor" href="#部署" aria-hidden="true">#</a> 部署</h2>
<h3 id="连接云服务器" tabindex="-1"><a class="header-anchor" href="#连接云服务器" aria-hidden="true">#</a> 连接云服务器</h3>
<p>用git bash ssh工具</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token function">ssh</span> root@ip地址公
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><img src="/25.png" alt="1"></p>
<h3 id="安装nodejs" tabindex="-1"><a class="header-anchor" href="#安装nodejs" aria-hidden="true">#</a> 安装nodejs</h3>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token comment"># 搜索软件包</span>
dnf search nodejs

<span class="token comment"># 查看软件包信息: nodejs的版本是10.21.0</span>
dnf info nodejs

<span class="token comment"># 安装nodejs</span>
dnf <span class="token function">install</span> nodejs
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="安装mysql" tabindex="-1"><a class="header-anchor" href="#安装mysql" aria-hidden="true">#</a> 安装mysql</h3>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token comment"># 查找MySQL</span>
dnf search mysql-server

<span class="token comment"># 查看MySQL，这里的版本是8.0.30</span>
dnf info mysql-server

<span class="token comment"># 安装MySQL，这里加-y的意思是依赖的内容也安装</span>
dnf <span class="token function">install</span> mysql-server -y
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="启动mysql-server" tabindex="-1"><a class="header-anchor" href="#启动mysql-server" aria-hidden="true">#</a> 启动mysql-server：</h3>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token comment"># 开启MySQL后台服务</span>
systemctl start mysqld

<span class="token comment"># 查看MySQL服务：active (running)表示启动成功</span>
systemctl status mysqld

<span class="token comment"># 随着系统一起启动</span>
systemctl <span class="token builtin class-name">enable</span> mysqld
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="配置mysql" tabindex="-1"><a class="header-anchor" href="#配置mysql" aria-hidden="true">#</a> 配置MySQL</h3>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code>mysql_secure_installation

<span class="token comment"># 接下来有一些选项，比如密码强度等等一些</span>
<span class="token comment"># MySQL8开始通常设置密码强度较强，选择2</span>
<span class="token comment"># 其他的选项可以自行选择</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p><img src="/30.png" alt="1"></p>
<p>选择y,然后2，设置密码，Dengjunyu123.
<img src="/31.png" alt="1">
<img src="/32.png" alt="1"></p>
<p><strong>连接数据库</strong></p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code>mysql -uroot -p
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>这个时候必须要配置root可以远程连接：</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token comment"># 使用mysql数据库</span>
use mysql<span class="token punctuation">;</span>
<span class="token comment"># 查看user表中，连接权限，默认看到root是localhost</span>
<span class="token keyword">select</span> host, user from user<span class="token punctuation">;</span>
<span class="token comment"># 修改权限</span>
update user <span class="token builtin class-name">set</span> <span class="token function">host</span> <span class="token operator">=</span> <span class="token string">'%'</span> where user <span class="token operator">=</span> <span class="token string">'root'</span><span class="token punctuation">;</span>

<span class="token comment"># 配置生效</span>
FLUSH PRIVILEGES<span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>但是呢，阿里云默认有在安全组中禁止掉3306端的连接的：</p>
<p>这时候我们需要去安全组中添加3306端口</p>
<p><img src="/32.png" alt="1"></p>
<h3 id="数据库迁移" tabindex="-1"><a class="header-anchor" href="#数据库迁移" aria-hidden="true">#</a> 数据库迁移</h3>
<p><img src="/34.png" alt="1"></p>
<p>然后新建一个数据库
<img src="/35.png" alt="1">
<img src="/36.png" alt="1"></p>
<h3 id="部署node项目" tabindex="-1"><a class="header-anchor" href="#部署node项目" aria-hidden="true">#</a> 部署node项目</h3>
<p>在vscode中安装<code v-pre>remote-ssh</code>插件
<img src="/37.png" alt="1"></p>
<h3 id="pm2启动node程序" tabindex="-1"><a class="header-anchor" href="#pm2启动node程序" aria-hidden="true">#</a> pm2启动node程序</h3>
<p>刚才我们是通过终端启动的node程序，那么如果终端被关闭掉了呢？</p>
<ul>
<li>那么这个时候相当于启动的Node进程会被关闭掉；</li>
<li>我们将无法继续访问服务器；</li>
</ul>
<p>在真实的部署过程中，我们会使用一个工具pm2来管理Node的进程：</p>
<ul>
<li>PM2是一个Node的进程管理器；</li>
<li>我们可以使用它来管理Node的后台进程；</li>
<li>这样在关闭终端时，Node进程会继续执行，那么服务器就可以继续为前端提供服务了；</li>
</ul>
<p>安装pm2：</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token function">npm</span> <span class="token function">install</span> pm2 -g
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>pm2常用的命令：</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token comment"># 命名进程</span>
pm2 start ./src/main.js --name my-api 
<span class="token comment"># 显示所有进程状态</span>
pm2 list               
<span class="token comment"># 停止指定的进程</span>
pm2 stop <span class="token number">0</span>       
<span class="token comment"># 停止所有进程</span>
pm2 stop all           
<span class="token comment"># 重启所有进程</span>
pm2 restart all      
<span class="token comment"># 重启指定的进程</span>
pm2 restart <span class="token number">0</span>          

<span class="token comment"># 杀死指定的进程</span>
pm2 delete <span class="token number">0</span>           
<span class="token comment"># 杀死全部进程</span>
pm2 delete all   

<span class="token comment">#后台运行pm2，启动4个app.js，实现负载均衡</span>
pm2 start app.js -i <span class="token number">4</span> 
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="jenkins自动化部署" tabindex="-1"><a class="header-anchor" href="#jenkins自动化部署" aria-hidden="true">#</a> jenkins自动化部署</h3>
<h4 id="安装java环境" tabindex="-1"><a class="header-anchor" href="#安装java环境" aria-hidden="true">#</a> 安装Java环境</h4>
<p>Jenkins本身是依赖Java的，所以我们需要先安装Java环境：</p>
<ul>
<li>这里我安装了Java1.8的环境</li>
</ul>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code>dnf search java-1.8
dnf <span class="token function">install</span> java-1.8.0-openjdk.x86_64
然后敲java验证是否安装成功
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h4 id="安装jenkins" tabindex="-1"><a class="header-anchor" href="#安装jenkins" aria-hidden="true">#</a> 安装Jenkins</h4>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token comment"># 下载 Jenkins 资源</span>
<span class="token function">sudo</span> <span class="token function">wget</span> -O /etc/yum.repos.d/jenkins.repo https://pkg.jenkins.io/redhat/jenkins.repo
<span class="token comment"># 获取并导入信任 的包制作者的秘钥</span>
<span class="token function">sudo</span> <span class="token function">rpm</span> --import https://pkg.jenkins.io/redhat/jenkins.io.key
<span class="token comment"># 升级 yum 源中的所有包</span>
<span class="token function">sudo</span> yum upgrade
<span class="token comment"># Jenkins 依赖于 java 所以需要安装 JDK</span>
<span class="token function">sudo</span> yum <span class="token function">install</span> java-11-openjdk
<span class="token comment"># 安装 Jenkins</span>
<span class="token function">sudo</span> yum <span class="token function">install</span> jenkins
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>如果最终 <code v-pre>Jenkins</code> 没有找到包而导致没有安装成功，检查第一步和第二部执行结果并重新执行。</p>
<h4 id="启动jenkins" tabindex="-1"><a class="header-anchor" href="#启动jenkins" aria-hidden="true">#</a> 启动Jenkins</h4>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token comment"># 启动 Jenkins 服务</span>
systemctl start jenkins
<span class="token comment"># 重启 Jenkins 服务</span>
systemctl restart jenkins
<span class="token comment"># 停止 Jenkins 服务</span>
systemctl stop jenkins
<span class="token comment"># 查看 Jenkins 服务状态</span>
systemctl status jenkins
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>启动成功之后在浏览器输入服务器ip地址加上在安全组配置的8080端口</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token number">8.134</span>.23.237:8080
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><img src="/38.png" alt="1"></p>
<p><code v-pre>cat /var/lib/jenkins/secrets/initialAdminPassword</code> 查看密码</p>
<p>随后进入插件安装页面，暂时安装系统推荐插件即可,然后创建用户</p>
<h2 id="nginx安装和配置" tabindex="-1"><a class="header-anchor" href="#nginx安装和配置" aria-hidden="true">#</a> nginx安装和配置</h2>
<h3 id="安装-1" tabindex="-1"><a class="header-anchor" href="#安装-1" aria-hidden="true">#</a> 安装</h3>
<p><strong>安装相应的工具包和库</strong></p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code>yum -y <span class="token function">install</span> gcc gcc-c++ autoconf pcre-devel <span class="token function">make</span> automake
yum -y <span class="token function">install</span> <span class="token function">wget</span> httpd-tools <span class="token function">vim</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><p>基本上没什么大问题就会显示“Complete!”</p>
<p>恭喜你，服务器环境基本安装完毕～</p>
<h4 id="搭建nginx配置" tabindex="-1"><a class="header-anchor" href="#搭建nginx配置" aria-hidden="true">#</a> <strong>搭建Nginx配置</strong></h4>
<p>首先看看服务器内yum内的Nginx源的版本</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code>yum list <span class="token operator">|</span> <span class="token function">grep</span> nginx
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>在终端输入如下</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token function">vim</span> /etc/yum.repos.d/nginx.repo
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>后填入下列代码，注意，我的centos是7.x版本，所以我写的是7，同学们可以按照自己的版本来</p>
<p><img src="/56.png" alt="1"></p>
<p>保存退出，然后安装 nginx</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code>yum <span class="token function">install</span> nginx
nginx -v
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><h4 id="nginx的配置文件" tabindex="-1"><a class="header-anchor" href="#nginx的配置文件" aria-hidden="true">#</a> <strong>Nginx的配置文件</strong></h4>
<p>通过<code v-pre>rpm -ql nginx</code> 指令查看 Nginx 都安装到了哪些目录</p>
<p>解释一下 <code v-pre>/etc/nginx/nginx.conf</code>，因为这个是 Nginx 的主配置，比较重要</p>
<p>输入命令行</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token builtin class-name">cd</span> /etc/nginx
<span class="token function">vim</span> nginx.conf
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><p>然后输入i编辑</p>
<p>把user后面的改成root
<img src="/4.png" alt="1"></p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code>server <span class="token punctuation">{</span>
        listen       <span class="token number">80</span><span class="token punctuation">;</span>
        listen       <span class="token punctuation">[</span>::<span class="token punctuation">]</span>:80<span class="token punctuation">;</span>
        server_name  _<span class="token punctuation">;</span>
        root         /usr/share/nginx/html<span class="token punctuation">;</span>  //这个就是我们默认访问的页面

        <span class="token comment"># Load configuration files for the default server block.</span>
        include /etc/nginx/default.d/*.conf<span class="token punctuation">;</span>

        error_page <span class="token number">404</span> /404.html<span class="token punctuation">;</span>
        location <span class="token operator">=</span> /404.html <span class="token punctuation">{</span>
        <span class="token punctuation">}</span>

        error_page <span class="token number">500</span> <span class="token number">502</span> <span class="token number">503</span> <span class="token number">504</span> /50x.html<span class="token punctuation">;</span>
        location <span class="token operator">=</span> /50x.html <span class="token punctuation">{</span>
        <span class="token punctuation">}</span>
    <span class="token punctuation">}</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code>server <span class="token punctuation">{</span>
        listen       <span class="token number">80</span><span class="token punctuation">;</span>
        listen       <span class="token punctuation">[</span>::<span class="token punctuation">]</span>:80<span class="token punctuation">;</span>
        server_name  _<span class="token punctuation">;</span>
       注释掉 root         /usr/share/nginx/html<span class="token punctuation">;</span>  //这个就是我们默认访问的页面 

        <span class="token comment"># Load configuration files for the default server block.</span>
        include /etc/nginx/default.d/*.conf<span class="token punctuation">;</span>
        添加
         location / <span class="token punctuation">{</span>
           root /root/djycms<span class="token punctuation">;</span> //我们文件地址
           index index.html<span class="token punctuation">;</span>
        <span class="token punctuation">}</span>

        error_page <span class="token number">404</span> /404.html<span class="token punctuation">;</span>
        location <span class="token operator">=</span> /404.html <span class="token punctuation">{</span>
        <span class="token punctuation">}</span>

        error_page <span class="token number">500</span> <span class="token number">502</span> <span class="token number">503</span> <span class="token number">504</span> /50x.html<span class="token punctuation">;</span>
        location <span class="token operator">=</span> /50x.html <span class="token punctuation">{</span>
        <span class="token punctuation">}</span>
    <span class="token punctuation">}</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>然后保存，输入<code v-pre>nginx -s reload</code> 会报错<code v-pre>nginx: [error] open() &quot;/var/run/nginx.pid&quot; failed (2: No such file or directory)</code>， 这个时候可以如下</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code>// 先输入
nginx
nginx -s reload
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>或者是如果你使用 iTerm 的话，可以配置 .bashrc 文件，添加一个 alias 的配置来简化运行nginx指令；或者是通过指令 <code v-pre>systemctl start nginx.service</code> 启动 nginx 服务，通过指令 <code v-pre>ps aux | grep nginx</code> 查看 nginx 是否是否启动；还有很多 nginx 的指令，大家自行去官网查看</p>
<p>启动nginx：</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code>systemctl start nginx
systemctl status nginx
systemctl <span class="token builtin class-name">enable</span> nginx
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>然后cd</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token builtin class-name">cd</span> /root/
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token function">mkdir</span> djycms  //ls查看是否创建文件夹成功
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token function">touch</span> index.html //ls查看是否创建成功
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>如果遇到问题先查看nginx是否在运行</p>
<div class="language-bash ext-sh line-numbers-mode"><pre v-pre class="language-bash"><code><span class="token function">ps</span> -ef <span class="token operator">|</span> <span class="token function">grep</span> nginx //查看是否运行
<span class="token function">service</span> nginx stop //停止
<span class="token function">ps</span> -ef <span class="token operator">|</span><span class="token function">grep</span> nginx //查看是否运行
nginx -s stop //停止
<span class="token function">service</span> nginx stop //停止
<span class="token function">chkconfig</span> nginx off
<span class="token function">rm</span> -rf /etc/init.d/nginx
<span class="token function">find</span> / -name nginx //查找关于nginx文件
<span class="token function">rm</span> -rf /usr/sbin/nginx //删除关于nginx的文件
yum remove nginx
systemctl status nginx
yum <span class="token function">install</span> -y nginx //重新安装
systemctl start nginx //启动
<span class="token builtin class-name">cd</span> /etc/nginx/ //进入nginx的conf目录（按照自己实际的路径来） nginx -t查找文件夹
<span class="token function">vim</span> nginx.conf
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>然后用vscode中的remote-ssh插件连接远程服务器</p>
<p><img src="/38.png" alt="1"></p>
<p>就可以看到刚才创建的djycms文件夹了</p>
</div></template>
