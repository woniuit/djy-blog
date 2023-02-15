<template><div><h1 id="vue3-admin-ts" tabindex="-1"><a class="header-anchor" href="#vue3-admin-ts" aria-hidden="true">#</a> vue3-admin-ts</h1>
<p><strong>ts版vue3+elementPlus+viet+pinia后台管理系统</strong></p>
<h2 id="第三方库集成" tabindex="-1"><a class="header-anchor" href="#第三方库集成" aria-hidden="true">#</a> 第三方库集成</h2>
<h3 id="vite-config-ts" tabindex="-1"><a class="header-anchor" href="#vite-config-ts" aria-hidden="true">#</a> vite.config.ts</h3>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">import</span> <span class="token punctuation">{</span> defineConfig <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">"vite"</span><span class="token punctuation">;</span>
<span class="token keyword">import</span> vue <span class="token keyword">from</span> <span class="token string">"@vitejs/plugin-vue"</span><span class="token punctuation">;</span>
<span class="token comment">// import path from "path";</span>
<span class="token keyword">import</span> AutoImport <span class="token keyword">from</span> <span class="token string">"unplugin-auto-import/vite"</span><span class="token punctuation">;</span>
<span class="token keyword">import</span> Components <span class="token keyword">from</span> <span class="token string">"unplugin-vue-components/vite"</span><span class="token punctuation">;</span>
<span class="token keyword">import</span> <span class="token punctuation">{</span> ElementPlusResolver <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">"unplugin-vue-components/resolvers"</span><span class="token punctuation">;</span>
<span class="token comment">// https://vitejs.dev/config/</span>
<span class="token keyword">export</span> <span class="token keyword">default</span> <span class="token function">defineConfig</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
    <span class="token comment">// root: path.join(__dirname, "src"),</span>
    <span class="token comment">// 配置代理服务器</span>
    <span class="token literal-property property">server</span><span class="token operator">:</span> <span class="token punctuation">{</span>
        <span class="token literal-property property">port</span><span class="token operator">:</span> <span class="token number">5173</span><span class="token punctuation">,</span>
        <span class="token literal-property property">proxy</span><span class="token operator">:</span> <span class="token punctuation">{</span>
            <span class="token comment">// 配置的代理不能超过10个</span>
            <span class="token string-property property">"/api"</span><span class="token operator">:</span> <span class="token punctuation">{</span>
                <span class="token literal-property property">target</span><span class="token operator">:</span> <span class="token string">"http://152.136.185.210:4000"</span><span class="token punctuation">,</span>
                <span class="token function-variable function">rewrite</span><span class="token operator">:</span> <span class="token punctuation">(</span><span class="token parameter">path</span><span class="token punctuation">)</span> <span class="token operator">=></span> path<span class="token punctuation">.</span><span class="token function">replace</span><span class="token punctuation">(</span><span class="token regex"><span class="token regex-delimiter">/</span><span class="token regex-source language-regex">^\/api</span><span class="token regex-delimiter">/</span></span><span class="token punctuation">,</span> <span class="token string">""</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
                <span class="token comment">// httppathRewrite: {</span>
                <span class="token comment">//     "^/api": "",</span>
                <span class="token comment">// },</span>
                <span class="token literal-property property">changeOrigin</span><span class="token operator">:</span> <span class="token boolean">true</span><span class="token punctuation">,</span> <span class="token comment">// 如果接口跨域，需要进行这个参数配置</span>
            <span class="token punctuation">}</span><span class="token punctuation">,</span>
        <span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token literal-property property">plugins</span><span class="token operator">:</span> <span class="token punctuation">[</span>
        <span class="token function">vue</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token comment">// ...</span>
        <span class="token function">AutoImport</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
            <span class="token literal-property property">resolvers</span><span class="token operator">:</span> <span class="token punctuation">[</span><span class="token function">ElementPlusResolver</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
        <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
        <span class="token function">Components</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
            <span class="token literal-property property">resolvers</span><span class="token operator">:</span> <span class="token punctuation">[</span><span class="token function">ElementPlusResolver</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
        <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    <span class="token punctuation">]</span><span class="token punctuation">,</span>
    <span class="token comment">// 别名</span>
    <span class="token comment">// resolve: {</span>
    <span class="token comment">//     // 别名配置</span>
    <span class="token comment">//     alias: {</span>
    <span class="token comment">//         "@static": path.join(__dirname, "src/static"),</span>
    <span class="token comment">//         "@": path.join(__dirname, "src"),</span>
    <span class="token comment">//     },</span>
    <span class="token comment">// },</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="element-plus" tabindex="-1"><a class="header-anchor" href="#element-plus" aria-hidden="true">#</a> element-plus</h3>
<p><strong>安装</strong></p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>pnpm install element-plus
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>全局完整引入</strong></p>
<p>在main.ts中</p>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">import</span> ElementPlus <span class="token keyword">from</span> <span class="token string">'element-plus'</span>
<span class="token keyword">import</span> <span class="token string">'element-plus/dist/index.css'</span>
app<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span>ElementPlus<span class="token punctuation">)</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p><strong>按需导入</strong></p>
<p>首先，需要安装两个插件</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>npm install -D unplugin-vue-components unplugin-auto-import
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>然后把下列代码插入到 <code v-pre>Vite</code></p>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token comment">//vite.config.ts</span>
<span class="token keyword">import</span> <span class="token punctuation">{</span> defineConfig <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">"vite"</span><span class="token punctuation">;</span>
<span class="token keyword">import</span> vue <span class="token keyword">from</span> <span class="token string">"@vitejs/plugin-vue"</span><span class="token punctuation">;</span>
<span class="token keyword">import</span> AutoImport <span class="token keyword">from</span> <span class="token string">"unplugin-auto-import/vite"</span><span class="token punctuation">;</span>
<span class="token keyword">import</span> Components <span class="token keyword">from</span> <span class="token string">"unplugin-vue-components/vite"</span><span class="token punctuation">;</span>
<span class="token keyword">import</span> <span class="token punctuation">{</span> ElementPlusResolver <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">"unplugin-vue-components/resolvers"</span><span class="token punctuation">;</span>
<span class="token comment">// https://vitejs.dev/config/</span>
<span class="token keyword">export</span> <span class="token keyword">default</span> <span class="token function">defineConfig</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
    <span class="token literal-property property">plugins</span><span class="token operator">:</span> <span class="token punctuation">[</span>
        <span class="token function">vue</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">,</span> <span class="token comment">// ...</span>
        <span class="token function">AutoImport</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
            <span class="token literal-property property">resolvers</span><span class="token operator">:</span> <span class="token punctuation">[</span><span class="token function">ElementPlusResolver</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
        <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
        <span class="token function">Components</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
            <span class="token literal-property property">resolvers</span><span class="token operator">:</span> <span class="token punctuation">[</span><span class="token function">ElementPlusResolver</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">]</span><span class="token punctuation">,</span>
        <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
    <span class="token punctuation">]</span><span class="token punctuation">,</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="axios" tabindex="-1"><a class="header-anchor" href="#axios" aria-hidden="true">#</a> axios</h3>
<p><strong>安装</strong></p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>npm install axios
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>封装axios</strong></p>
<h4 id="一-入门版" tabindex="-1"><a class="header-anchor" href="#一-入门版" aria-hidden="true">#</a> <strong>一.入门版</strong></h4>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">import</span> axios<span class="token punctuation">,</span> <span class="token punctuation">{</span> AxiosInstance<span class="token punctuation">,</span> AxiosRequestConfig <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">"axios"</span><span class="token punctuation">;</span>
  <span class="token comment">//AxiosRequestConfig请求配置，比如:</span>
  <span class="token comment">//url?: string;</span>
  <span class="token comment">//method?: Method | string;</span>
  <span class="token comment">//baseURL?: string;</span>
  <span class="token comment">//transformRequest?: AxiosRequestTransformer | AxiosRequestTransformer[];</span>
  <span class="token comment">//transformResponse?: AxiosResponseTransformer | AxiosResponseTransformer[];</span>
  <span class="token comment">//headers?: AxiosRequestHeaders;</span>
  <span class="token comment">//params?: any;</span>
  <span class="token comment">//paramsSerializer?: (params: any) => string;</span>
  <span class="token comment">//data?: D;</span>
  <span class="token comment">//timeout?: number;</span>
<span class="token keyword">class</span> <span class="token class-name">myHttp</span> <span class="token punctuation">{</span>
    <span class="token literal-property property">instance</span><span class="token operator">:</span> AxiosInstance<span class="token punctuation">;</span>
    <span class="token function">constructor</span><span class="token punctuation">(</span><span class="token parameter"><span class="token literal-property property">config</span><span class="token operator">:</span> AxiosRequestConfig</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
        <span class="token comment">// 创建axios实例</span>
        <span class="token keyword">this</span><span class="token punctuation">.</span>instance <span class="token operator">=</span> axios<span class="token punctuation">.</span><span class="token function">create</span><span class="token punctuation">(</span>config<span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
    <span class="token function">request</span><span class="token punctuation">(</span>config<span class="token operator">:</span> AxiosRequestConfig<span class="token punctuation">)</span><span class="token operator">:</span> <span class="token keyword">void</span><span class="token punctuation">{</span>
        <span class="token keyword">this</span><span class="token punctuation">.</span>instance<span class="token punctuation">.</span><span class="token function">request</span><span class="token punctuation">(</span>config<span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">then</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token parameter">res</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
            console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span>res<span class="token punctuation">)</span>
        <span class="token punctuation">}</span><span class="token punctuation">)</span>
    <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
<span class="token keyword">export</span> <span class="token keyword">default</span> myHttp<span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p><strong>使用</strong></p>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">import</span> myHttp <span class="token keyword">from</span> <span class="token string">"./axios"</span><span class="token punctuation">;</span>
<span class="token keyword">export</span> <span class="token keyword">const</span> http1 <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">myHttp</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
    <span class="token literal-property property">baseURL</span><span class="token operator">:</span> <span class="token string">"/api"</span><span class="token punctuation">,</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">import</span> <span class="token punctuation">{</span> http1 <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">"./http/index"</span><span class="token punctuation">;</span>
http1<span class="token punctuation">.</span><span class="token function">request</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
    <span class="token literal-property property">url</span><span class="token operator">:</span> <span class="token string">"/login"</span><span class="token punctuation">,</span>
    <span class="token literal-property property">method</span><span class="token operator">:</span> <span class="token string">"post"</span><span class="token punctuation">,</span>
    <span class="token literal-property property">data</span><span class="token operator">:</span> <span class="token punctuation">{</span>
        <span class="token literal-property property">name</span><span class="token operator">:</span> <span class="token string">""</span><span class="token punctuation">,</span>
        <span class="token literal-property property">password</span><span class="token operator">:</span> <span class="token string">""</span><span class="token punctuation">,</span>
    <span class="token punctuation">}</span><span class="token punctuation">,</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h4 id="二-扩展" tabindex="-1"><a class="header-anchor" href="#二-扩展" aria-hidden="true">#</a> <strong>二.扩展</strong></h4>
<ul>
<li>加loading和Message</li>
<li>配置不同的baseurl</li>
<li>配置全局的loading和单独请求不需要loading</li>
<li>配置不同的请求头</li>
</ul>
<div class="language-typescript ext-ts line-numbers-mode"><pre v-pre class="language-typescript"><code><span class="token keyword">import</span> axios<span class="token punctuation">,</span> <span class="token punctuation">{</span> AxiosInstance<span class="token punctuation">,</span> AxiosRequestConfig<span class="token punctuation">,</span> AxiosResponse <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">"axios"</span><span class="token punctuation">;</span>
<span class="token keyword">import</span> <span class="token punctuation">{</span> ElLoading<span class="token punctuation">,</span> ElMessage <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">"element-plus"</span><span class="token punctuation">;</span>
<span class="token comment">//Loading</span>
<span class="token keyword">function</span> <span class="token function">startLoading</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">const</span> loading <span class="token operator">=</span> ElLoading<span class="token punctuation">.</span><span class="token function">service</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
        lock<span class="token operator">:</span> <span class="token boolean">true</span><span class="token punctuation">,</span>
        text<span class="token operator">:</span> <span class="token string">"正在请求数据..."</span><span class="token punctuation">,</span>
        background<span class="token operator">:</span> <span class="token string">"rgba(0, 0, 0, 0.7)"</span><span class="token punctuation">,</span>
    <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token keyword">return</span> loading<span class="token punctuation">;</span>
<span class="token punctuation">}</span>
<span class="token comment">//</span>
<span class="token keyword">interface</span> <span class="token class-name">interceptorType<span class="token operator">&lt;</span><span class="token constant">T</span> <span class="token operator">=</span> AxiosResponse<span class="token operator">></span></span> <span class="token punctuation">{</span>
    requestInterceptor<span class="token operator">?</span><span class="token operator">:</span> <span class="token punctuation">(</span>config<span class="token operator">:</span> AxiosRequestConfig<span class="token punctuation">)</span> <span class="token operator">=></span> AxiosRequestConfig<span class="token punctuation">;</span>
    requestInterceptorCatch<span class="token operator">?</span><span class="token operator">:</span> <span class="token punctuation">(</span>error<span class="token operator">:</span> <span class="token builtin">any</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token builtin">any</span><span class="token punctuation">;</span>
    responseInterceptor<span class="token operator">?</span><span class="token operator">:</span> <span class="token punctuation">(</span>res<span class="token operator">:</span> <span class="token constant">T</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token constant">T</span><span class="token punctuation">;</span>
    responseInterceptorCatch<span class="token operator">?</span><span class="token operator">:</span> <span class="token punctuation">(</span>error<span class="token operator">:</span> <span class="token builtin">any</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token builtin">any</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
<span class="token keyword">interface</span> <span class="token class-name">interceptorTypeConfig<span class="token operator">&lt;</span><span class="token constant">T</span> <span class="token operator">=</span> AxiosResponse<span class="token operator">></span></span> <span class="token keyword">extends</span> <span class="token class-name">AxiosRequestConfig</span> <span class="token punctuation">{</span>
    interceptors<span class="token operator">?</span><span class="token operator">:</span> interceptorType<span class="token operator">&lt;</span><span class="token constant">T</span><span class="token operator">></span><span class="token punctuation">;</span>
    showLoading<span class="token operator">?</span><span class="token operator">:</span> <span class="token builtin">boolean</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
<span class="token keyword">class</span> <span class="token class-name">myHttp</span> <span class="token punctuation">{</span>
    instance<span class="token operator">:</span> AxiosInstance<span class="token punctuation">;</span>
    interceptors<span class="token operator">?</span><span class="token operator">:</span> interceptorType<span class="token punctuation">;</span>
    showLoading<span class="token operator">:</span> Boolean<span class="token punctuation">;</span>
    <span class="token function">constructor</span><span class="token punctuation">(</span>config<span class="token operator">:</span> interceptorTypeConfig<span class="token punctuation">)</span> <span class="token punctuation">{</span>
        <span class="token comment">// 创建axios实例</span>
        <span class="token keyword">this</span><span class="token punctuation">.</span>instance <span class="token operator">=</span> axios<span class="token punctuation">.</span><span class="token function">create</span><span class="token punctuation">(</span>config<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token comment">// console.log('config=>>',config)</span>
        <span class="token comment">//添加拦截</span>
        <span class="token keyword">this</span><span class="token punctuation">.</span>interceptors <span class="token operator">=</span> config<span class="token punctuation">.</span>interceptors<span class="token punctuation">;</span>
        <span class="token keyword">this</span><span class="token punctuation">.</span>showLoading <span class="token operator">=</span> config<span class="token punctuation">.</span>showLoading <span class="token operator">??</span> <span class="token boolean">true</span><span class="token punctuation">;</span>
        <span class="token comment">// 使用拦截器</span>
        <span class="token comment">// 从config中取出的拦截器是对应的实例的拦截器</span>
        <span class="token comment">//请求拦截器</span>
        <span class="token keyword">this</span><span class="token punctuation">.</span>instance<span class="token punctuation">.</span>interceptors<span class="token punctuation">.</span>request<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span><span class="token keyword">this</span><span class="token punctuation">.</span>interceptors<span class="token operator">?.</span>requestInterceptor<span class="token punctuation">,</span> <span class="token keyword">this</span><span class="token punctuation">.</span>interceptors<span class="token operator">?.</span>requestInterceptorCatch<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token comment">//响应拦截器</span>
        <span class="token keyword">this</span><span class="token punctuation">.</span>instance<span class="token punctuation">.</span>interceptors<span class="token punctuation">.</span>response<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span><span class="token keyword">this</span><span class="token punctuation">.</span>interceptors<span class="token operator">?.</span>responseInterceptor<span class="token punctuation">,</span> <span class="token keyword">this</span><span class="token punctuation">.</span>interceptors<span class="token operator">?.</span>responseInterceptorCatch<span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token comment">//全局共用的拦截器</span>
        <span class="token comment">//请求拦截</span>
        <span class="token keyword">this</span><span class="token punctuation">.</span>instance<span class="token punctuation">.</span>interceptors<span class="token punctuation">.</span>request<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span>
            <span class="token punctuation">(</span>config<span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
                <span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token keyword">this</span><span class="token punctuation">.</span>showLoading<span class="token punctuation">)</span> <span class="token punctuation">{</span>
                    <span class="token function">startLoading</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                <span class="token punctuation">}</span>

                <span class="token keyword">return</span> config<span class="token punctuation">;</span>
            <span class="token punctuation">}</span><span class="token punctuation">,</span>
            <span class="token punctuation">(</span>error<span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
                <span class="token builtin">Promise</span><span class="token punctuation">.</span><span class="token function">reject</span><span class="token punctuation">(</span>error<span class="token punctuation">)</span><span class="token punctuation">;</span>
            <span class="token punctuation">}</span>
        <span class="token punctuation">)</span><span class="token punctuation">;</span>
        <span class="token comment">// 响应拦截</span>
        <span class="token keyword">this</span><span class="token punctuation">.</span>instance<span class="token punctuation">.</span>interceptors<span class="token punctuation">.</span>response<span class="token punctuation">.</span><span class="token function">use</span><span class="token punctuation">(</span>
            <span class="token punctuation">(</span>res<span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
                <span class="token comment">// 将loading移除</span>
                <span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token keyword">this</span><span class="token punctuation">.</span>showLoading<span class="token punctuation">)</span> <span class="token punctuation">{</span>
                    <span class="token function">startLoading</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">close</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                <span class="token punctuation">}</span>
                <span class="token comment">//</span>

                <span class="token builtin">console</span><span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"res"</span><span class="token punctuation">,</span> res<span class="token punctuation">)</span><span class="token punctuation">;</span>
            <span class="token punctuation">}</span><span class="token punctuation">,</span>
            <span class="token punctuation">(</span>error<span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
                <span class="token comment">// 将loading移除</span>
                <span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token keyword">this</span><span class="token punctuation">.</span>showLoading<span class="token punctuation">)</span> <span class="token punctuation">{</span>
                    <span class="token function">startLoading</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">close</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                <span class="token punctuation">}</span>
                <span class="token keyword">if</span> <span class="token punctuation">(</span>error <span class="token operator">&amp;&amp;</span> error<span class="token punctuation">.</span>response<span class="token punctuation">)</span> <span class="token punctuation">{</span>
                    <span class="token comment">// 1.公共错误处理</span>
                    <span class="token comment">// 2.根据响应码具体处理</span>
                    <span class="token keyword">switch</span> <span class="token punctuation">(</span>error<span class="token punctuation">.</span>response<span class="token punctuation">.</span>status<span class="token punctuation">)</span> <span class="token punctuation">{</span>
                        <span class="token keyword">case</span> <span class="token number">400</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"错误请求"</span><span class="token punctuation">;</span>
                            <span class="token keyword">break</span><span class="token punctuation">;</span>
                        <span class="token keyword">case</span> <span class="token number">401</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"未授权，请重新登录"</span><span class="token punctuation">;</span>
                            <span class="token keyword">break</span><span class="token punctuation">;</span>
                        <span class="token keyword">case</span> <span class="token number">403</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"拒绝访问"</span><span class="token punctuation">;</span>
                            <span class="token keyword">break</span><span class="token punctuation">;</span>
                        <span class="token keyword">case</span> <span class="token number">404</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"请求错误,未找到该资源"</span><span class="token punctuation">;</span>
                            <span class="token comment">// window.location.href = "/NotFound";</span>
                            <span class="token keyword">break</span><span class="token punctuation">;</span>
                        <span class="token keyword">case</span> <span class="token number">405</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"请求方法未允许"</span><span class="token punctuation">;</span>
                            <span class="token keyword">break</span><span class="token punctuation">;</span>
                        <span class="token keyword">case</span> <span class="token number">408</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"请求超时"</span><span class="token punctuation">;</span>
                            <span class="token keyword">break</span><span class="token punctuation">;</span>
                        <span class="token keyword">case</span> <span class="token number">500</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"服务器端出错"</span><span class="token punctuation">;</span>
                            <span class="token keyword">break</span><span class="token punctuation">;</span>
                        <span class="token keyword">case</span> <span class="token number">501</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"网络未实现"</span><span class="token punctuation">;</span>
                            <span class="token keyword">break</span><span class="token punctuation">;</span>
                        <span class="token keyword">case</span> <span class="token number">502</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"网络错误"</span><span class="token punctuation">;</span>
                            <span class="token keyword">break</span><span class="token punctuation">;</span>
                        <span class="token keyword">case</span> <span class="token number">503</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"服务不可用"</span><span class="token punctuation">;</span>
                            <span class="token keyword">break</span><span class="token punctuation">;</span>
                        <span class="token keyword">case</span> <span class="token number">504</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"网络超时"</span><span class="token punctuation">;</span>
                            <span class="token keyword">break</span><span class="token punctuation">;</span>
                        <span class="token keyword">case</span> <span class="token number">505</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"http版本不支持该请求"</span><span class="token punctuation">;</span>
                            <span class="token keyword">break</span><span class="token punctuation">;</span>
                        <span class="token keyword">default</span><span class="token operator">:</span>
                            error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token template-string"><span class="token template-punctuation string">`</span><span class="token string">连接错误</span><span class="token interpolation"><span class="token interpolation-punctuation punctuation">${</span>error<span class="token punctuation">.</span>response<span class="token punctuation">.</span>status<span class="token interpolation-punctuation punctuation">}</span></span><span class="token template-punctuation string">`</span></span><span class="token punctuation">;</span>
                    <span class="token punctuation">}</span>
                <span class="token punctuation">}</span> <span class="token keyword">else</span> <span class="token punctuation">{</span>
                    <span class="token comment">// 超时处理</span>
                    <span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token constant">JSON</span><span class="token punctuation">.</span><span class="token function">stringify</span><span class="token punctuation">(</span>error<span class="token punctuation">)</span><span class="token punctuation">.</span><span class="token function">includes</span><span class="token punctuation">(</span><span class="token string">"timeout"</span><span class="token punctuation">)</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
                        ElMessage<span class="token punctuation">.</span><span class="token function">error</span><span class="token punctuation">(</span><span class="token string">"服务器响应超时，请刷新当前页"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
                    <span class="token punctuation">}</span>
                    error<span class="token punctuation">.</span>ElMessage <span class="token operator">=</span> <span class="token string">"连接服务器失败"</span><span class="token punctuation">;</span>
                <span class="token punctuation">}</span>

                ElMessage<span class="token punctuation">.</span><span class="token function">error</span><span class="token punctuation">(</span>error<span class="token punctuation">.</span>response<span class="token punctuation">.</span>data<span class="token punctuation">)</span><span class="token punctuation">;</span>
                <span class="token comment">/***** 处理结束 *****/</span>
                <span class="token comment">//如果不需要错误处理，以上的处理过程都可省略</span>
                <span class="token keyword">return</span> <span class="token builtin">Promise</span><span class="token punctuation">.</span><span class="token function">resolve</span><span class="token punctuation">(</span>error<span class="token punctuation">.</span>response<span class="token punctuation">)</span><span class="token punctuation">;</span>
                <span class="token comment">// return err;</span>
            <span class="token punctuation">}</span>
        <span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span>
    <span class="token generic-function"><span class="token function">request</span><span class="token generic class-name"><span class="token operator">&lt;</span><span class="token constant">T</span> <span class="token operator">=</span> <span class="token builtin">any</span><span class="token operator">></span></span></span><span class="token punctuation">(</span>config<span class="token operator">:</span> interceptorTypeConfig<span class="token operator">&lt;</span><span class="token constant">T</span><span class="token operator">></span><span class="token punctuation">)</span><span class="token operator">:</span> <span class="token builtin">Promise</span><span class="token operator">&lt;</span><span class="token constant">T</span><span class="token operator">></span> <span class="token punctuation">{</span>
        <span class="token keyword">return</span> <span class="token keyword">new</span> <span class="token class-name"><span class="token builtin">Promise</span></span><span class="token punctuation">(</span><span class="token punctuation">(</span>resolve<span class="token punctuation">,</span> reject<span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
    
          <span class="token comment">// 判断是否需要显示loading</span>
          <span class="token keyword">if</span> <span class="token punctuation">(</span>config<span class="token punctuation">.</span>showLoading <span class="token operator">===</span> <span class="token boolean">false</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
            <span class="token keyword">this</span><span class="token punctuation">.</span>showLoading <span class="token operator">=</span> config<span class="token punctuation">.</span>showLoading
          <span class="token punctuation">}</span>
    
          <span class="token keyword">this</span><span class="token punctuation">.</span>instance
            <span class="token punctuation">.</span><span class="token generic-function"><span class="token function">request</span><span class="token generic class-name"><span class="token operator">&lt;</span><span class="token builtin">any</span><span class="token punctuation">,</span> <span class="token constant">T</span><span class="token operator">></span></span></span><span class="token punctuation">(</span>config<span class="token punctuation">)</span>
            <span class="token punctuation">.</span><span class="token function">then</span><span class="token punctuation">(</span><span class="token punctuation">(</span>res<span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
              <span class="token comment">// 单个请求对数据的处理</span>
            <span class="token comment">//   if (config.interceptors?.responseInterceptor) {</span>
            <span class="token comment">//     res = config.interceptors.responseInterceptor(res)</span>
            <span class="token comment">//   }</span>
              <span class="token comment">// 将showLoading设置true, 这样不会影响下一个请求</span>
              <span class="token keyword">this</span><span class="token punctuation">.</span>showLoading <span class="token operator">=</span> <span class="token boolean">true</span>
    
              <span class="token comment">// 将结果resolve返回出去</span>
              <span class="token function">resolve</span><span class="token punctuation">(</span>res<span class="token punctuation">)</span>
            <span class="token punctuation">}</span><span class="token punctuation">)</span>
            <span class="token punctuation">.</span><span class="token function">catch</span><span class="token punctuation">(</span><span class="token punctuation">(</span>err<span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
              <span class="token comment">// 将showLoading设置true, 这样不会影响下一个请求</span>
              <span class="token keyword">this</span><span class="token punctuation">.</span>showLoading <span class="token operator">=</span> <span class="token boolean">true</span>
              <span class="token function">reject</span><span class="token punctuation">(</span>err<span class="token punctuation">)</span>
              <span class="token keyword">return</span> err
            <span class="token punctuation">}</span><span class="token punctuation">)</span>
        <span class="token punctuation">}</span><span class="token punctuation">)</span>
      <span class="token punctuation">}</span>
<span class="token punctuation">}</span>
<span class="token keyword">export</span> <span class="token keyword">default</span> myHttp<span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p><strong>使用</strong></p>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">import</span> myHttp <span class="token keyword">from</span> <span class="token string">"./axios"</span><span class="token punctuation">;</span>
<span class="token comment">//可以new多个http,互不影响</span>
<span class="token keyword">export</span> <span class="token keyword">const</span> axios <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">myHttp</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
    <span class="token literal-property property">baseURL</span><span class="token operator">:</span> <span class="token string">"/api"</span><span class="token punctuation">,</span>
    <span class="token literal-property property">headers</span><span class="token operator">:</span> <span class="token punctuation">{</span>
        <span class="token string-property property">"Content-Type"</span><span class="token operator">:</span> <span class="token string">"application/json"</span><span class="token punctuation">,</span>
    <span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token literal-property property">interceptors</span><span class="token operator">:</span> <span class="token punctuation">{</span>
        <span class="token function-variable function">requestInterceptor</span><span class="token operator">:</span> <span class="token punctuation">(</span><span class="token parameter">config</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
            <span class="token comment">// 携带token的拦截</span>
            console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"请求拦截1"</span><span class="token punctuation">,</span> config<span class="token punctuation">)</span><span class="token punctuation">;</span>
            <span class="token keyword">return</span> config<span class="token punctuation">;</span>
        <span class="token punctuation">}</span><span class="token punctuation">,</span>
        <span class="token function-variable function">requestInterceptorCatch</span><span class="token operator">:</span> <span class="token punctuation">(</span><span class="token parameter">err</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
            console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"请求错误拦截1"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
            <span class="token keyword">return</span> err<span class="token punctuation">;</span>
        <span class="token punctuation">}</span><span class="token punctuation">,</span>
        <span class="token function-variable function">responseInterceptor</span><span class="token operator">:</span> <span class="token punctuation">(</span><span class="token parameter">res</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
            console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"响应拦截1"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
            <span class="token keyword">return</span> res<span class="token punctuation">;</span>
        <span class="token punctuation">}</span><span class="token punctuation">,</span>
        <span class="token function-variable function">responseInterceptorCatch</span><span class="token operator">:</span> <span class="token punctuation">(</span><span class="token parameter">err</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
            console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"错误响应拦截1"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
            <span class="token keyword">return</span> err<span class="token punctuation">;</span>
        <span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token punctuation">}</span><span class="token punctuation">,</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code>axios<span class="token punctuation">.</span><span class="token function">request</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
    <span class="token literal-property property">showLoading</span><span class="token operator">:</span> <span class="token boolean">true</span><span class="token punctuation">,</span> <span class="token comment">//是否开启loading</span>
    <span class="token literal-property property">url</span><span class="token operator">:</span> <span class="token string">"/login"</span><span class="token punctuation">,</span>
    <span class="token literal-property property">method</span><span class="token operator">:</span> <span class="token string">"post"</span><span class="token punctuation">,</span>
    <span class="token literal-property property">data</span><span class="token operator">:</span> <span class="token punctuation">{</span>
   
    <span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token comment">//单独的请求头</span>
    <span class="token comment">//   headers: {</span>
    <span class="token comment">//     "Content-Type": "application/json123",</span>
    <span class="token comment">// },</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h4 id="三-api文件管理" tabindex="-1"><a class="header-anchor" href="#三-api文件管理" aria-hidden="true">#</a> 三.api文件管理</h4>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">import</span> <span class="token punctuation">{</span> axios <span class="token punctuation">}</span> <span class="token keyword">from</span> <span class="token string">"./http/index"</span><span class="token punctuation">;</span>

<span class="token keyword">export</span> <span class="token keyword">function</span> <span class="token function">axiosdemo</span><span class="token punctuation">(</span><span class="token parameter">data</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
   axios<span class="token punctuation">.</span><span class="token function">request</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
    <span class="token literal-property property">showLoading</span><span class="token operator">:</span> <span class="token boolean">true</span><span class="token punctuation">,</span> <span class="token comment">//是否开启loading</span>
    <span class="token literal-property property">url</span><span class="token operator">:</span> <span class="token string">"/login"</span><span class="token punctuation">,</span>
    <span class="token literal-property property">method</span><span class="token operator">:</span> <span class="token string">"post"</span><span class="token punctuation">,</span>
    <span class="token literal-property property">data</span><span class="token operator">:</span> <span class="token punctuation">{</span>
   
    <span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token comment">//单独的请求头</span>
    <span class="token comment">//   headers: {</span>
    <span class="token comment">//     "Content-Type": "application/json123",</span>
    <span class="token comment">// },</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="vue-router" tabindex="-1"><a class="header-anchor" href="#vue-router" aria-hidden="true">#</a> vue-router</h3>
<h3 id="pinia" tabindex="-1"><a class="header-anchor" href="#pinia" aria-hidden="true">#</a> pinia</h3>
</div></template>
