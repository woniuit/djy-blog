<template><div><h1 id="sql" tabindex="-1"><a class="header-anchor" href="#sql" aria-hidden="true">#</a> sql</h1>
<h2 id="mongodb" tabindex="-1"><a class="header-anchor" href="#mongodb" aria-hidden="true">#</a> MongoDB</h2>
<p><strong><a href="https://yangyongli.blog.csdn.net/article/details/113917773?spm=1001.2101.3001.6650.1&amp;utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-113917773-blog-114709588.t5_layer_eslanding_A_4&amp;depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-113917773-blog-114709588.t5_layer_eslanding_A_4&amp;utm_relevant_index=2" target="_blank" rel="noopener noreferrer">安装<ExternalLinkIcon/></a></strong></p>
<h3 id="常用的语句" tabindex="-1"><a class="header-anchor" href="#常用的语句" aria-hidden="true">#</a> <strong>常用的语句</strong></h3>
<p><strong>查看当前数据库列表</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">show</span> dbs
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查看当前操作的数据库</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>切换数据库（如果没有这个数据库 会 创建数据库）</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">use</span> 数据库名称
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>如果真的想把这个数据库创建成功，那么必须插入一个数据。 数据库中不能直接插入数据，只能往<a href="https://so.csdn.net/so/search?q=%E9%9B%86%E5%90%88&amp;spm=1001.2101.3001.7020" target="_blank" rel="noopener noreferrer">集合<ExternalLinkIcon/></a>(collections)中插入数据。
下面命令表示给 itying 数据库的 user 表中插入数据。</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span><span class="token keyword">user</span><span class="token punctuation">.</span><span class="token keyword">insert</span><span class="token punctuation">(</span>{<span class="token string">"name"</span>:<span class="token string">"xiaoming"</span>}<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>显示当前的数据集合</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">show</span> collections
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>删除指定的集合 删除表</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span><span class="token keyword">user</span><span class="token punctuation">.</span><span class="token keyword">drop</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>删除当前所在的数据库</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span>dropDatabase<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>插入（增加）数据</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span>表名<span class="token punctuation">.</span><span class="token keyword">insert</span><span class="token punctuation">(</span>{<span class="token string">"name"</span>:<span class="token string">"zhangsan"</span>，<span class="token string">"age"</span>:<span class="token number">20</span>}<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询所有记录</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span><span class="token keyword">user</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 age = 22 的记录</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span><span class="token keyword">user</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span>{<span class="token string">"age"</span>: <span class="token number">22</span>}<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 age &gt; 22 的记录</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span><span class="token keyword">user</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span>{<span class="token string">"age"</span>: {$gt: <span class="token number">22</span>}}<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 age &lt; 22 的记录</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span><span class="token keyword">user</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span>{<span class="token string">"age"</span>: {$lt: <span class="token number">22</span>}}<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 age &gt;= 25 的记录</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span><span class="token keyword">user</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span>{<span class="token string">"age"</span>: {$gte: <span class="token number">25</span>}}<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 age &lt;= 25 的记录</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span><span class="token keyword">user</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span>{<span class="token string">"age"</span>: {$lte: <span class="token number">25</span>}}<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 age &gt;= 23 并且 age &lt;= 26</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span><span class="token keyword">user</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span>{<span class="token string">"age"</span>: {$gte: <span class="token number">23</span><span class="token punctuation">,</span> $lte: <span class="token number">26</span>}}<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 name 中包含 mongo 的数据 模糊查询用于搜索</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span><span class="token keyword">user</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span>{<span class="token string">"name"</span>: <span class="token operator">/</span>mongo<span class="token operator">/</span>}<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 name 中以 mongo 开头的</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span><span class="token keyword">user</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span>{<span class="token string">"name"</span>: <span class="token operator">/</span><span class="token operator">^</span>mongo<span class="token operator">/</span>}<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 name 中以 mongo 结尾的</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code>db<span class="token punctuation">.</span><span class="token keyword">user</span><span class="token punctuation">.</span>find<span class="token punctuation">(</span>{<span class="token string">"name"</span>: <span class="token operator">/</span>mongo$<span class="token operator">/</span>}<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><a href="https://blog.csdn.net/ZYS10000/article/details/116425819" target="_blank" rel="noopener noreferrer">更多语句<ExternalLinkIcon/></a></p>
<h3 id="mongoose" tabindex="-1"><a class="header-anchor" href="#mongoose" aria-hidden="true">#</a> mongoose</h3>
<p><strong>安装</strong></p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>npm install mongoose --save
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">const</span> mongoose <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">"mongoose"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">async</span> <span class="token keyword">function</span> <span class="token function">main</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">await</span> mongoose<span class="token punctuation">.</span><span class="token function">connect</span><span class="token punctuation">(</span><span class="token string">"mongodb://localhost:27017/test"</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>
<span class="token function">main</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">then</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token parameter">res</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
        console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"连接成功"</span><span class="token punctuation">,</span> res<span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span><span class="token punctuation">)</span>
    <span class="token punctuation">.</span><span class="token function">catch</span><span class="token punctuation">(</span><span class="token punctuation">(</span><span class="token parameter">err</span><span class="token punctuation">)</span> <span class="token operator">=></span> <span class="token punctuation">{</span>
        console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">"连接失败"</span><span class="token punctuation">,</span> err<span class="token punctuation">)</span><span class="token punctuation">;</span>
    <span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> cc <span class="token operator">=</span> <span class="token keyword">new</span> <span class="token class-name">mongoose<span class="token punctuation">.</span>Schema</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
    <span class="token literal-property property">name</span><span class="token operator">:</span> <span class="token punctuation">{</span>
        <span class="token literal-property property">type</span><span class="token operator">:</span> String<span class="token punctuation">,</span>
        <span class="token literal-property property">require</span><span class="token operator">:</span><span class="token boolean">true</span>
    <span class="token punctuation">}</span><span class="token punctuation">,</span>
    <span class="token literal-property property">age</span><span class="token operator">:</span> <span class="token punctuation">{</span>
        <span class="token literal-property property">type</span><span class="token operator">:</span> Number<span class="token punctuation">,</span>
        <span class="token literal-property property">require</span><span class="token operator">:</span><span class="token boolean">true</span>
    <span class="token punctuation">}</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">const</span> modelName <span class="token operator">=</span> mongoose<span class="token punctuation">.</span><span class="token function">model</span><span class="token punctuation">(</span><span class="token string">'djyTest'</span><span class="token punctuation">,</span> cc<span class="token punctuation">)</span><span class="token punctuation">;</span>
modelName<span class="token punctuation">.</span><span class="token function">create</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
    <span class="token literal-property property">name</span><span class="token operator">:</span><span class="token string">"学习完成1"</span><span class="token punctuation">,</span>
    <span class="token literal-property property">age</span><span class="token operator">:</span><span class="token number">20</span>
<span class="token punctuation">}</span><span class="token punctuation">,</span><span class="token keyword">function</span> <span class="token punctuation">(</span><span class="token parameter">err</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">if</span> <span class="token punctuation">(</span><span class="token operator">!</span>err<span class="token punctuation">)</span><span class="token punctuation">{</span>
        console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">'插入成功'</span><span class="token punctuation">)</span>
    <span class="token punctuation">}</span><span class="token keyword">else</span> <span class="token punctuation">{</span>
        console<span class="token punctuation">.</span><span class="token function">log</span><span class="token punctuation">(</span><span class="token string">'失败'</span><span class="token punctuation">)</span>
    <span class="token punctuation">}</span>
 
<span class="token punctuation">}</span><span class="token punctuation">)</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h2 id="mysql" tabindex="-1"><a class="header-anchor" href="#mysql" aria-hidden="true">#</a> mysql</h2>
<h3 id="常见的数据库" tabindex="-1"><a class="header-anchor" href="#常见的数据库" aria-hidden="true">#</a> 常见的数据库</h3>
<p>通常将数据划分成两类：关系型数据库和非关系型数据库。</p>
<p>关系型数据库：MySQL、Oracle、DB2、SQL Server、Postgre SQL等</p>
<ul>
<li>关系型数据库通常我们会创建很多个二维数据表</li>
<li>数据表之间相互关联起来，形成一对一、一对多、多对对等关系；</li>
<li>之后可以利用SQL语句在多张表中查询我们所需的数据</li>
<li>支持事务，对数据的访问更加的安全</li>
</ul>
<p>非关系型数据库：MongoDB、Redis、Memcached、HBse等；</p>
<ul>
<li>非关系型数据库的英文其实是Not only SQL，也简称为NoSQL；</li>
<li>相当而已非关系型数据库比较简单一些，存储数据也会更加自由（甚至我们可以直接将一个复杂的json对象直接塞入到数据库中）；</li>
<li>NoSQL是基于Key-Value的对应关系，并且查询的过程中不需要经过SQL解析，所以性能更高；</li>
<li>NoSQL通常不支持事物，需要在自己的程序中来保证一些原子性的操作</li>
</ul>
<p>如何在开发中选择他们呢？具体的选择会根据不同的项目进行综合的分析，</p>
<ul>
<li>目前在公司进行后端开发（Node、Java、Go等），还是以关系型数据库为主</li>
<li>比较常用的用到非关系型数据库的，在爬取大量的数据进行存储时，会比较常见；</li>
</ul>
<h3 id="安装" tabindex="-1"><a class="header-anchor" href="#安装" aria-hidden="true">#</a> 安装</h3>
<p><a href="https://dev.mysql.com/downloads/mysql/" target="_blank" rel="noopener noreferrer">下载地址<ExternalLinkIcon/></a></p>
<p>选择<code v-pre>GO to Download Page</code>下载</p>
<p>推荐大家直接下载安装版本，在安装过程中会配置一些环境变量；</p>
<ul>
<li>Windows推荐下载MSI的版本；</li>
<li>Mac推荐下载DMG的版本；
<img src="/3-1.png" alt="1"></li>
</ul>
<p><strong>Windows安装过程</strong>
<img src="/3-2.png" alt="1">
<img src="/3-3.png" alt="1">
<img src="/3-4.png" alt="1">
<img src="/3-5.png" alt="1">
<img src="/3-6.png" alt="1"></p>
<p><strong>mysql的连接操作</strong></p>
<p>一、环境变量配置</p>
<p>在任务栏搜索中搜索MySQL</p>
<p><img src="/3-7.png" alt="1">
<img src="/3-8.png" alt="1"></p>
<p>二、终端连接数据库</p>
<p><code v-pre>mysql -uroot -p</code>
<img src="/3-9.png" alt="1">
如上图连接成功</p>
<p>三、终端数据库操作</p>
<p><code v-pre>show databases;</code>//查看数据库</p>
<h3 id="gut工具navicat" tabindex="-1"><a class="header-anchor" href="#gut工具navicat" aria-hidden="true">#</a> Gut工具Navicat</h3>
<p><a href="https://www.navicat.com.cn/download/direct-download?product=navicat_premium_cs_x64.exe&amp;location=1" target="_blank" rel="noopener noreferrer">下载地址<ExternalLinkIcon/></a></p>
<p>使用</p>
<p>点击新建连接，创建连接，然后点击查询，新建查询就可以操作sql语句。</p>
<h3 id="数据库的操作" tabindex="-1"><a class="header-anchor" href="#数据库的操作" aria-hidden="true">#</a> 数据库的操作</h3>
<p>查看当前数据库：</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 查看所有的数据</span>
<span class="token keyword">SHOW</span> <span class="token keyword">DATABASES</span><span class="token punctuation">;</span>
<span class="token comment"># 使用某一个数据</span>
<span class="token keyword">USE</span> coderhub<span class="token punctuation">;</span>
<span class="token comment"># 查看当前正在使用的数据库</span>
<span class="token keyword">SELECT</span> <span class="token keyword">DATABASE</span><span class="token punctuation">(</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>创建新的数据库：</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">CREATE</span> <span class="token keyword">DATABASE</span> <span class="token keyword">IF</span> <span class="token operator">NOT</span> <span class="token keyword">EXISTS</span> bilibili
<span class="token keyword">DEFAULT</span> <span class="token keyword">CHARACTER</span> <span class="token keyword">SET</span> utf8mb4 <span class="token keyword">COLLATE</span> utf8mb4_0900_ai_ci<span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><p>删除数据库：</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 删除数据库</span>
<span class="token keyword">DROP</span> <span class="token keyword">DATABASE</span> bilibili<span class="token punctuation">;</span>
<span class="token keyword">DROP</span> <span class="token keyword">DATABASE</span> <span class="token keyword">IF</span> <span class="token keyword">EXIT</span> bilibili<span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>修改数据库：</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 修改数据库的字符集和排序规则</span>
<span class="token keyword">ALTER</span> <span class="token keyword">DATABASE</span> bilibili <span class="token keyword">CHARACTER</span> <span class="token keyword">SET</span> <span class="token operator">=</span> utf8 <span class="token keyword">COLLATE</span> <span class="token operator">=</span> utf8_unicode_ci<span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="数据表的操作" tabindex="-1"><a class="header-anchor" href="#数据表的操作" aria-hidden="true">#</a> 数据表的操作</h3>
<p>查看数据表</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 查看所有的数据表</span>
<span class="token keyword">SHOW</span> <span class="token keyword">TABLES</span><span class="token punctuation">;</span>
<span class="token comment"># 查看某一个表结构</span>
<span class="token keyword">DESC</span> <span class="token keyword">user</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>创建数据表</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> <span class="token keyword">IF</span> <span class="token operator">NOT</span> <span class="token keyword">EXISTS</span> <span class="token identifier"><span class="token punctuation">`</span>users<span class="token punctuation">`</span></span><span class="token punctuation">(</span>
name <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
age <span class="token keyword">INT</span><span class="token punctuation">,</span>
height <span class="token keyword">DOUBLE</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>删除数据表</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 删除数据库</span>
<span class="token keyword">DROP</span> <span class="token keyword">TABLE</span> users<span class="token punctuation">;</span>
<span class="token keyword">DROP</span> <span class="token keyword">TABLE</span> <span class="token keyword">IF</span> <span class="token keyword">EXISTS</span> users<span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>修改表</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 1.修改表名</span>
<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> <span class="token identifier"><span class="token punctuation">`</span>moments<span class="token punctuation">`</span></span> <span class="token keyword">RENAME</span> <span class="token keyword">TO</span> <span class="token identifier"><span class="token punctuation">`</span>moment<span class="token punctuation">`</span></span><span class="token punctuation">;</span>
<span class="token comment"># 2.添加一个新的列</span>
<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> <span class="token identifier"><span class="token punctuation">`</span>moment<span class="token punctuation">`</span></span> <span class="token keyword">ADD</span> <span class="token identifier"><span class="token punctuation">`</span>publishTime<span class="token punctuation">`</span></span> <span class="token keyword">DATETIME</span><span class="token punctuation">;</span>
<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> <span class="token identifier"><span class="token punctuation">`</span>moment<span class="token punctuation">`</span></span> <span class="token keyword">ADD</span> <span class="token identifier"><span class="token punctuation">`</span>updateTime<span class="token punctuation">`</span></span> <span class="token keyword">DATETIME</span><span class="token punctuation">;</span>
<span class="token comment"># 3.删除一列数据</span>
<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> <span class="token identifier"><span class="token punctuation">`</span>moment<span class="token punctuation">`</span></span> <span class="token keyword">DROP</span> <span class="token identifier"><span class="token punctuation">`</span>updateTime<span class="token punctuation">`</span></span><span class="token punctuation">;</span>
<span class="token comment"># 4.修改列的名称</span>
<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> <span class="token identifier"><span class="token punctuation">`</span>moment<span class="token punctuation">`</span></span> CHANGE <span class="token identifier"><span class="token punctuation">`</span>publishTime<span class="token punctuation">`</span></span> <span class="token identifier"><span class="token punctuation">`</span>publishDate<span class="token punctuation">`</span></span> <span class="token keyword">DATE</span><span class="token punctuation">;</span>
<span class="token comment"># 5.修改列的数据类型</span>
<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> <span class="token identifier"><span class="token punctuation">`</span>moment<span class="token punctuation">`</span></span> <span class="token keyword">MODIFY</span> <span class="token identifier"><span class="token punctuation">`</span>id<span class="token punctuation">`</span></span> <span class="token keyword">INT</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>插入数据</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">INSERT</span> <span class="token keyword">INTO</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token punctuation">(</span><span class="token identifier"><span class="token punctuation">`</span>title<span class="token punctuation">`</span></span><span class="token punctuation">,</span> <span class="token identifier"><span class="token punctuation">`</span>description<span class="token punctuation">`</span></span><span class="token punctuation">,</span> <span class="token identifier"><span class="token punctuation">`</span>price<span class="token punctuation">`</span></span><span class="token punctuation">,</span> <span class="token identifier"><span class="token punctuation">`</span>publishTime<span class="token punctuation">`</span></span><span class="token punctuation">)</span> 
<span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token string">'iPhone'</span><span class="token punctuation">,</span> <span class="token string">'iPhone12只要998'</span><span class="token punctuation">,</span> <span class="token number">998.88</span><span class="token punctuation">,</span> <span class="token string">'2020-10-10'</span><span class="token punctuation">)</span><span class="token punctuation">;</span> 
<span class="token keyword">INSERT</span> <span class="token keyword">INTO</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token punctuation">(</span><span class="token identifier"><span class="token punctuation">`</span>title<span class="token punctuation">`</span></span><span class="token punctuation">,</span> <span class="token identifier"><span class="token punctuation">`</span>description<span class="token punctuation">`</span></span><span class="token punctuation">,</span> <span class="token identifier"><span class="token punctuation">`</span>price<span class="token punctuation">`</span></span><span class="token punctuation">,</span> <span class="token identifier"><span class="token punctuation">`</span>publishTime<span class="token punctuation">`</span></span><span class="token punctuation">)</span> 
<span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token string">'huawei'</span><span class="token punctuation">,</span> <span class="token string">'iPhoneP40只要888'</span><span class="token punctuation">,</span> <span class="token number">888.88</span><span class="token punctuation">,</span> <span class="token string">'2020-11-11'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>删除数据</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 删除数据</span>
<span class="token comment"># 会删除表中所有的数据</span>
<span class="token keyword">DELETE</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span><span class="token punctuation">;</span>
<span class="token comment"># 会删除符合条件的数据</span>
<span class="token keyword">DELETE</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> <span class="token identifier"><span class="token punctuation">`</span>title<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token string">'iPhone'</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>修改数据</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 修改数据</span>
<span class="token comment"># 会修改表中所有的数据</span>
<span class="token keyword">UPDATE</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">SET</span> <span class="token identifier"><span class="token punctuation">`</span>title<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token string">'iPhone12'</span><span class="token punctuation">,</span> <span class="token identifier"><span class="token punctuation">`</span>price<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token number">1299.88</span><span class="token punctuation">;</span>
<span class="token comment"># 会修改符合条件的数据</span>
<span class="token keyword">UPDATE</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">SET</span> <span class="token identifier"><span class="token punctuation">`</span>title<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token string">'iPhone12'</span><span class="token punctuation">,</span> <span class="token identifier"><span class="token punctuation">`</span>price<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token number">1299.88</span> <span class="token keyword">WHERE</span> <span class="token identifier"><span class="token punctuation">`</span>title<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token string">'iPhone'</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>如果我们希望修改完数据后，直接可以显示最新的更新时间：</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">ADD</span> <span class="token identifier"><span class="token punctuation">`</span>updateTime<span class="token punctuation">`</span></span> <span class="token keyword">TIMESTAMP</span> 
<span class="token keyword">DEFAULT</span> <span class="token keyword">CURRENT_TIMESTAMP</span> <span class="token keyword">ON</span> <span class="token keyword">UPDATE</span> <span class="token keyword">CURRENT_TIMESTAMP</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="数据查询" tabindex="-1"><a class="header-anchor" href="#数据查询" aria-hidden="true">#</a> 数据查询</h3>
<p>结合下面代码连接数据库操作</p>
<p>查询所有的数据并且显示所有的字段：</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>查询指定字段</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">SELECT</span> 字段<span class="token number">1</span><span class="token punctuation">,</span>字段<span class="token number">2</span>
<span class="token keyword">SELECT</span> title<span class="token punctuation">,</span> brand<span class="token punctuation">,</span> price <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><p>我们也可以给字段起别名： 别名一般在多张表或者给客户端返回对应的key时会使用到</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">SELECT</span> title <span class="token keyword">as</span> t<span class="token punctuation">,</span> brand <span class="token keyword">as</span> b<span class="token punctuation">,</span> price <span class="token keyword">as</span> p <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h4 id="条件查询" tabindex="-1"><a class="header-anchor" href="#条件查询" aria-hidden="true">#</a> <strong>条件查询</strong></h4>
<p>条件查询会使用 WEHRE查询子句</p>
<p><strong>WHERE的比较运算符</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 查询价格小于1000的手机</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> price <span class="token operator">&lt;</span> <span class="token number">1000</span><span class="token punctuation">;</span>
<span class="token comment"># 查询价格大于等于2000的手机</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> price <span class="token operator">>=</span> <span class="token number">2000</span><span class="token punctuation">;</span>
<span class="token comment"># 价格等于3399的手机</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> price <span class="token operator">=</span> <span class="token number">3399</span><span class="token punctuation">;</span>
<span class="token comment"># 价格不等于3399的手机</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> price <span class="token operator">!=</span> <span class="token number">3399</span><span class="token punctuation">;</span>
<span class="token comment"># 查询华为品牌的手机</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token string">'华为'</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p><strong>WHERE的逻辑运算符</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 查询品牌是华为，并且小于2000元的手机</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token string">'华为'</span> <span class="token operator">and</span> <span class="token identifier"><span class="token punctuation">`</span>price<span class="token punctuation">`</span></span> <span class="token operator">&lt;</span> <span class="token number">2000</span><span class="token punctuation">;</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token string">'华为'</span> <span class="token operator">&amp;&amp;</span> <span class="token identifier"><span class="token punctuation">`</span>price<span class="token punctuation">`</span></span> <span class="token operator">&lt;</span> <span class="token number">2000</span><span class="token punctuation">;</span>
<span class="token comment"># 查询1000到2000的手机（不包含1000和2000）</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> price <span class="token operator">></span> <span class="token number">1000</span> <span class="token operator">and</span> price <span class="token operator">&lt;</span> <span class="token number">2000</span><span class="token punctuation">;</span>
<span class="token comment"># OR: 符合一个条件即可</span>
<span class="token comment"># 查询所有的华为手机或者价格小于1000的手机</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> brand <span class="token operator">=</span> <span class="token string">'华为'</span> <span class="token operator">or</span> price <span class="token operator">&lt;</span> <span class="token number">1000</span><span class="token punctuation">;</span>
<span class="token comment"># 查询1000到2000的手机（包含1000和2000）</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> price <span class="token operator">BETWEEN</span> <span class="token number">1000</span> <span class="token operator">and</span> <span class="token number">2000</span><span class="token punctuation">;</span>
<span class="token comment"># 查看多个结果中的一个</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> brand <span class="token operator">in</span> <span class="token punctuation">(</span><span class="token string">'华为'</span><span class="token punctuation">,</span> <span class="token string">'小米'</span><span class="token punctuation">)</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p><strong>模糊查询</strong>使用LIKE关键字，结合两个特殊的符号：</p>
<p>%表示匹配任意个的任意字符；</p>
<p>_表示匹配一个的任意字符</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 查询所有以v开头的title</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> title <span class="token operator">LIKE</span> <span class="token string">'v%'</span><span class="token punctuation">;</span>
<span class="token comment"># 查询带M的title</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> title <span class="token operator">LIKE</span> <span class="token string">'%M%'</span><span class="token punctuation">;</span>
<span class="token comment"># 查询带M的title必须是第三个字符</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> title <span class="token operator">LIKE</span> <span class="token string">'__M%'</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h4 id="查询结果排序" tabindex="-1"><a class="header-anchor" href="#查询结果排序" aria-hidden="true">#</a> 查询结果排序</h4>
<p>当我们查询到结果的时候，我们希望讲结果按照某种方式进行排序，这个时候使用的是ORDER BY</p>
<p>ORDER BY有两个常用的值：</p>
<p>ASC：升序排列；</p>
<p>DESC：降序排列；</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> brand <span class="token operator">=</span> <span class="token string">'华为'</span> <span class="token operator">or</span> price <span class="token operator">&lt;</span> <span class="token number">1000</span> <span class="token keyword">ORDER</span> <span class="token keyword">BY</span> price <span class="token keyword">ASC</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h4 id="分页查询" tabindex="-1"><a class="header-anchor" href="#分页查询" aria-hidden="true">#</a> 分页查询</h4>
<p>当数据库中的数据非常多时，一次性查询到所有的结果进行显示是不太现实的：</p>
<p>在真实开发中，我们都会要求用户传入offset、limit或者page等字段；</p>
<p>它们的目的是让我们可以在数据库中进行分页查询；</p>
<p>它的用法有[LIMIT {[offset,] row_count | row_count OFFSET offset}]</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">LIMIT</span> <span class="token number">30</span> <span class="token keyword">OFFSET</span> <span class="token number">0</span><span class="token punctuation">;</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">LIMIT</span> <span class="token number">30</span> <span class="token keyword">OFFSET</span> <span class="token number">30</span><span class="token punctuation">;</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">LIMIT</span> <span class="token number">30</span> <span class="token keyword">OFFSET</span> <span class="token number">60</span><span class="token punctuation">;</span>
<span class="token comment"># 另外一种写法：offset, row_count</span>
<span class="token keyword">SELECT</span> <span class="token operator">*</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">LIMIT</span> <span class="token number">90</span><span class="token punctuation">,</span> <span class="token number">30</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="代码连接数据库" tabindex="-1"><a class="header-anchor" href="#代码连接数据库" aria-hidden="true">#</a> 代码连接数据库</h3>
<p>创建一个mysql文件夹，<code v-pre>npm init -y</code>,然后<code v-pre>npm install mysql2</code></p>
<p>创建一张新的表</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> <span class="token keyword">IF</span> <span class="token operator">NOT</span> <span class="token keyword">EXISTS</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token punctuation">(</span>
id <span class="token keyword">INT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token keyword">AUTO_INCREMENT</span><span class="token punctuation">,</span>
brand <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
title <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">100</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
price <span class="token keyword">DOUBLE</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
score <span class="token keyword">DECIMAL</span><span class="token punctuation">(</span><span class="token number">2</span><span class="token punctuation">,</span><span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
voteCnt <span class="token keyword">INT</span><span class="token punctuation">,</span>
url <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">100</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
pid <span class="token keyword">INT</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>创建一个<code v-pre>phone.json</code>文件，数据如下</p>
<div class="language-json ext-json line-numbers-mode"><pre v-pre class="language-json"><code><span class="token punctuation">[</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为nova 3（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2699</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.7</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">65</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1185512.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1185512"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为P20 Pro（6GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">4488</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">103</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1207038.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1207038"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为P20（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3388</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.4</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">127</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1175779.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1175779"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为nova 3i（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1999</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">9</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1222100.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1222100"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为Mate 10（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3399</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">125</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1165672.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1165672"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为nova 3e（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1999</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">71</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1207608.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1207608"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为nova 2s（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2399</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">97</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1204363.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1204363"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为Mate 10 Pro（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3599</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.7</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">92</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1181128.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1181128"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为畅享8（3GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1099</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">28</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1208286.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1208286"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为P10（VTR-AL00/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3488</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.2</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">395</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1160028.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1160028"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为畅享8 Plus（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1499</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">11</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1210102.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1210102"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为麦芒7（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2399</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.6</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">5</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1227167.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1227167"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为Mate 9（MHA-AL00/4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1788</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">449</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1143413.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1143413"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为nova 3i（6GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2199</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">9</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1224424.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1224424"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为Mate RS保时捷版（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">9999</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">16</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1210089.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1210089"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为nova 2（PIC-AL00/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1228</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">209</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1170042.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1170042"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为麦芒6（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2199</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">57</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1182274.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1182274"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为P9（EVA-AL00/标准版/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1448</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">648</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index404275.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"404275"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为nova（CAZ-AL10/高配版/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">988</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.9</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">198</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1154505.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1154505"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为畅享8e（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">999</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">4.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">4</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1210103.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1210103"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为麦芒5（MLA-AL10/高配版/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1099</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">136</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1148829.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1148829"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为P10 Plus（VKY-AL00/6GB RAM全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2488</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">186</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1163813.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1163813"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"华为"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"华为Mate 9 Pro（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2799</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">136</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1159578.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1159578"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo X7 Plus（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2350</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.2</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">484</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1147812.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1147812"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo X9s Plus（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2498</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.4</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">523</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1170837.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1170837"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo Y51A（高配版/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">998</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.6</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">306</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1115625.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1115625"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo X7（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1799</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.7</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">736</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1145877.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1145877"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo X9s（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1998</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.9</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">563</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1174429.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1174429"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo Y66i（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1198</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">161</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1204388.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1204388"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo X9s  L（移动全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1998</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.9</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">563</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1175257.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1175257"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo X9L（移动全网通）  "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1998</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">1362</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1170124.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1170124"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo X20Plus屏幕指纹版（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3598</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.2</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">17</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1205808.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1205808"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo Y75（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1098</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">27</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1208237.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1208237"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo X20（旗舰版/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2598</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">1075</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1184293.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1184293"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo Y55（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">999</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.4</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">126</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1156093.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1156093"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo Y75（3GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1298</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">27</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1185212.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1185212"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"vivo"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"vivo Xplay6（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3498</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.7</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">691</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1159623.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1159623"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO R17（8GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3499</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">173</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1225806.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1225806"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO Find X（标准版/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">4999</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">774</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1213467.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1213467"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO R15（6GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2699</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.2</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">1055</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1206990.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1206990"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO A3（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1799</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.9</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">366</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1211599.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1211599"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO A5（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1500</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.7</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">357</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1221126.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1221126"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO R11（标准版/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1553</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">1346</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1150077.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1150077"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO A1（3GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1000</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.4</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">86</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1209829.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1209829"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO Find X兰博基尼版（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">9999</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.7</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">89</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1220645.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1220645"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO R17 Pro（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">4299</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.4</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">91</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1225826.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1225826"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO A7x（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1999</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.7</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">48</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1230724.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1230724"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO R11s（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2299</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.2</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">1310</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1184068.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1184068"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO A83 (全网通) "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1199</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">38</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1205003.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1205003"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO A57（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">799</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.6</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">577</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1160598.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1160598"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO A73（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1499</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.4</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">380</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1205054.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1205054"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO R17（雾光渐变色/8GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3599</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">171</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1229193.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1229193"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO R11s Plus（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1899</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">669</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1184231.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1184231"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO R15梦镜版（梦境红/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2999</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.2</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">1032</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1208720.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1208720"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO R17（6GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3199</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">171</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1229159.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1229159"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO R11 Plus（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1788</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.2</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">546</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1170222.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1170222"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO R15梦镜版（陶瓷黑/梦境紫/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3299</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">9.2</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">1032</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1210656.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1210656"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"OPPO"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"OPPO A79（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1699</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.7</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">339</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1203640.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1203640"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米8（6GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2599</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">308</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1213787.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1213787"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米6X（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1349</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">106</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1170480.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1170480"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米8 SE（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1699</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">76</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1217453.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1217453"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米8青春版（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1399</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">18</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1231048.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1231048"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米红米Note 5（3GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">999</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">98</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1175353.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1175353"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米MIX 2s（6GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2999</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.6</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">134</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1202983.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1202983"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米6（6GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2409</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.2</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">526</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1161066.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1161066"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米红米6 Pro（3GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">969</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">21</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1220665.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1220665"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米8透明探索版（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3699</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.4</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">48</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1216973.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1216973"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米Max 3（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1699</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">66</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1205304.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1205304"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米MIX 2（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2299</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.4</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">147</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1160797.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1160797"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米Max 2（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">939</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.2</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">119</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1165765.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1165765"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米红米6（3GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">769</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.4</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">11</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1215069.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1215069"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米红米5 Plus（3GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">800</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">75</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1183689.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1183689"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米红米Note 5（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1299</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">98</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1209455.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1209455"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米红米Note 4X（3GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">999</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.7</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">285</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1163122.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1163122"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米Note 3（6GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1849</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">92</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1164780.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1164780"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米5X（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1129</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">98</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1175015.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1175015"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米红米6A（2GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">549</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">3</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1216196.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1216196"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米6X（6GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1709</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">106</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1212271.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1212271"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"小米"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"小米MIX（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2900</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">173</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1158428.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1158428"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone XS（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">8699</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">51</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1229519.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1229519"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone X（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">6898</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">193</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1182639.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1182639"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone XR（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">6499</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">4.6</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">35</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1205394.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1205394"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone 8 Plus（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">5468</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">84</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1182632.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1182632"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone XS Max（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">9599</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">30</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1229520.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1229520"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone 8（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">4528</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">254</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index394162.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"394162"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone 7（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3628</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">475</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index384973.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"384973"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone 7 Plus（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">4499</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">335</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1104332.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1104332"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone 6S Plus（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3000</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">279</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index398690.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"398690"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone 5S（双4G） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1199</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.2</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">2964</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index340414.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"340414"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone 8 Plus（国际版/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">5188</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">84</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1204817.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1204817"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone 7 Plus（双4G） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">4388</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">335</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1177080.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1177080"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone 8（国际版/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">4688</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">254</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1204816.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1204816"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone X（国际版/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">6888</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">191</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1204818.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1204818"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone 7 Plus（国际版/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">4749</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">335</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1155434.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1155434"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"苹果"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"苹果iPhone 6S（国际版/双4G） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2320</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">551</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1100448.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1100448"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技坚果Pro 2S（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1798</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">22</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1227474.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1227474"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技坚果R1（6GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">3499</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">64</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1162957.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1162957"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技坚果Pro 2（4GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1399</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.4</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">85</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1202624.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1202624"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技坚果3（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1099</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.5</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">42</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1209757.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1209757"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技坚果Pro 2S（6GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1998</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">6.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">22</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1228692.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1228692"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技坚果Pro（64GB ROM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1179</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">188</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1166591.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1166591"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技坚果R1（8GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">4499</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">5.1</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">64</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1214020.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1214020"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技坚果Pro 2特别版（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1449</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.4</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">85</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1213907.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1213907"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技坚果Pro（128GB ROM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1499</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">188</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1170719.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1170719"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技坚果Pro 2（6GB RAM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1949</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.4</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">85</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1202737.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1202737"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技M1（全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1800</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">148</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1138532.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1138532"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技M1L（高配版/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">2399</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">8</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">148</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1157726.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1157726"</span>
  <span class="token punctuation">}</span><span class="token punctuation">,</span>
  <span class="token punctuation">{</span>
    <span class="token property">"brand"</span><span class="token operator">:</span> <span class="token string">"锤子科技"</span><span class="token punctuation">,</span>
    <span class="token property">"title"</span><span class="token operator">:</span> <span class="token string">"锤子科技坚果Pro（32GB ROM/全网通） "</span><span class="token punctuation">,</span>
    <span class="token property">"price"</span><span class="token operator">:</span> <span class="token number">1099</span><span class="token punctuation">,</span>
    <span class="token property">"score"</span><span class="token operator">:</span> <span class="token number">7.3</span><span class="token punctuation">,</span>
    <span class="token property">"voteCnt"</span><span class="token operator">:</span> <span class="token number">188</span><span class="token punctuation">,</span>
    <span class="token property">"url"</span><span class="token operator">:</span> <span class="token string">"http://detail.zol.com.cn/cell_phone/index1170718.shtml"</span><span class="token punctuation">,</span>
    <span class="token property">"pid"</span><span class="token operator">:</span> <span class="token string">"1170718"</span>
  <span class="token punctuation">}</span>
<span class="token punctuation">]</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>创建一个index.js文件,如下</p>
<div class="language-javascript ext-js line-numbers-mode"><pre v-pre class="language-javascript"><code><span class="token keyword">const</span> mysql <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'mysql2'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
 
<span class="token keyword">const</span> connection <span class="token operator">=</span> mysql<span class="token punctuation">.</span><span class="token function">createConnection</span><span class="token punctuation">(</span><span class="token punctuation">{</span>
  <span class="token literal-property property">host</span><span class="token operator">:</span> <span class="token string">'localhost'</span><span class="token punctuation">,</span>
  <span class="token literal-property property">port</span><span class="token operator">:</span> <span class="token number">3306</span><span class="token punctuation">,</span>
  <span class="token literal-property property">user</span><span class="token operator">:</span> <span class="token string">'root'</span><span class="token punctuation">,</span>
  <span class="token literal-property property">password</span><span class="token operator">:</span> <span class="token string">'Dengjunyu123.'</span><span class="token punctuation">,</span>
  <span class="token literal-property property">database</span><span class="token operator">:</span> <span class="token string">'bilibili'</span>  <span class="token comment">//数据库名称</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> statement <span class="token operator">=</span> <span class="token template-string"><span class="token template-punctuation string">`</span><span class="token string">INSERT INTO products SET ?;</span><span class="token template-punctuation string">`</span></span> <span class="token comment">//表名称，插到哪个表中</span>
<span class="token keyword">const</span> phoneJson <span class="token operator">=</span> <span class="token function">require</span><span class="token punctuation">(</span><span class="token string">'./phone.json'</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">for</span> <span class="token punctuation">(</span><span class="token keyword">let</span> phone <span class="token keyword">of</span> phoneJson<span class="token punctuation">)</span> <span class="token punctuation">{</span>
  connection<span class="token punctuation">.</span><span class="token function">query</span><span class="token punctuation">(</span>statement<span class="token punctuation">,</span> phone<span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token punctuation">}</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>然后执行<code v-pre>node index.js</code>，去刷新数据库中对应的表就可以看到数据添加成功</p>
<h3 id="聚合函数" tabindex="-1"><a class="header-anchor" href="#聚合函数" aria-hidden="true">#</a> 聚合函数</h3>
<p>聚合函数表示对 值的集合 进行操作的 组（集合）函数。</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 华为手机价格的平均值</span>
<span class="token keyword">SELECT</span> <span class="token function">AVG</span><span class="token punctuation">(</span>price<span class="token punctuation">)</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> brand <span class="token operator">=</span> <span class="token string">'华为'</span><span class="token punctuation">;</span>
<span class="token comment"># 计算所有手机的平均分</span>
<span class="token keyword">SELECT</span> <span class="token function">AVG</span><span class="token punctuation">(</span>score<span class="token punctuation">)</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span><span class="token punctuation">;</span>
<span class="token comment"># 手机中最低和最高分数</span>
<span class="token keyword">SELECT</span> <span class="token function">MAX</span><span class="token punctuation">(</span>score<span class="token punctuation">)</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span><span class="token punctuation">;</span>
<span class="token keyword">SELECT</span> <span class="token function">MIN</span><span class="token punctuation">(</span>score<span class="token punctuation">)</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span><span class="token punctuation">;</span>
<span class="token comment"># 计算总投票人数</span>
<span class="token keyword">SELECT</span> <span class="token function">SUM</span><span class="token punctuation">(</span>voteCnt<span class="token punctuation">)</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span><span class="token punctuation">;</span>
<span class="token comment"># 计算所有条目的数量</span>
<span class="token keyword">SELECT</span> <span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token operator">*</span><span class="token punctuation">)</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span><span class="token punctuation">;</span>
<span class="token comment"># 华为手机的个数</span>
<span class="token keyword">SELECT</span> <span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token operator">*</span><span class="token punctuation">)</span> <span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">WHERE</span> brand <span class="token operator">=</span> <span class="token string">'华为'</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="group-by" tabindex="-1"><a class="header-anchor" href="#group-by" aria-hidden="true">#</a> Group By</h3>
<h4 id="认识group-by" tabindex="-1"><a class="header-anchor" href="#认识group-by" aria-hidden="true">#</a> 认识Group By</h4>
<p><strong>事实上聚合函数相当于默认将所有的数据分成了一组：</strong></p>
<p>我们前面使用avg还是max等，都是将所有的结果看成一组来计算的；</p>
<p>那么如果我们希望划分多个组：比如华为、苹果、小米等手机分别的平均价格，应该怎么来做呢？</p>
<p>这个时候我们可以使用 GROUP BY；</p>
<p><strong>GROUP BY通常和聚合函数一起使用：</strong></p>
<p>表示我们先对数据进行分组，再对每一组数据，进行聚合函数的计算；</p>
<p><strong>我们现在来提一个需求：</strong></p>
<p>根据品牌进行分组；</p>
<p>计算各个品牌中：商品的个数、平均价格；</p>
<p>也包括：最高价格、最低价格、平均评分；</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">SELECT</span> brand<span class="token punctuation">,</span> 
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token operator">*</span><span class="token punctuation">)</span> <span class="token keyword">as</span> count<span class="token punctuation">,</span> 
<span class="token function">ROUND</span><span class="token punctuation">(</span><span class="token function">AVG</span><span class="token punctuation">(</span>price<span class="token punctuation">)</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">)</span> <span class="token keyword">as</span> avgPrice<span class="token punctuation">,</span>
<span class="token function">MAX</span><span class="token punctuation">(</span>price<span class="token punctuation">)</span> <span class="token keyword">as</span> maxPrice<span class="token punctuation">,</span>
<span class="token function">MIN</span><span class="token punctuation">(</span>price<span class="token punctuation">)</span> <span class="token keyword">as</span> minPrice<span class="token punctuation">,</span>
<span class="token function">AVG</span><span class="token punctuation">(</span>score<span class="token punctuation">)</span> <span class="token keyword">as</span> avgScore
<span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">GROUP</span> <span class="token keyword">BY</span> brand<span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h4 id="group-by的约束条件" tabindex="-1"><a class="header-anchor" href="#group-by的约束条件" aria-hidden="true">#</a> Group By的约束条件</h4>
<p>如果我们希望给Group By查询到的结果添加一些约束，那么我们可以使用：<code v-pre>HAVING</code>。</p>
<p>比如：如果我们还希望筛选出平均价格在4000以下，并且平均分在7以上的品牌：</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">SELECT</span> brand<span class="token punctuation">,</span> 
<span class="token function">COUNT</span><span class="token punctuation">(</span><span class="token operator">*</span><span class="token punctuation">)</span> <span class="token keyword">as</span> count<span class="token punctuation">,</span> 
<span class="token function">ROUND</span><span class="token punctuation">(</span><span class="token function">AVG</span><span class="token punctuation">(</span>price<span class="token punctuation">)</span><span class="token punctuation">,</span><span class="token number">2</span><span class="token punctuation">)</span> <span class="token keyword">as</span> avgPrice<span class="token punctuation">,</span>
<span class="token function">MAX</span><span class="token punctuation">(</span>price<span class="token punctuation">)</span> <span class="token keyword">as</span> maxPrice<span class="token punctuation">,</span>
<span class="token function">MIN</span><span class="token punctuation">(</span>price<span class="token punctuation">)</span> <span class="token keyword">as</span> minPrice<span class="token punctuation">,</span>
<span class="token function">AVG</span><span class="token punctuation">(</span>score<span class="token punctuation">)</span> <span class="token keyword">as</span> avgScore
<span class="token keyword">FROM</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">GROUP</span> <span class="token keyword">BY</span> brand 
<span class="token keyword">HAVING</span> avgPrice <span class="token operator">&lt;</span> <span class="token number">4000</span> <span class="token operator">and</span> avgScore <span class="token operator">></span> <span class="token number">7</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="创建多张表" tabindex="-1"><a class="header-anchor" href="#创建多张表" aria-hidden="true">#</a> 创建多张表</h3>
<p>假如我们的上面的商品表中，对应的品牌还需要包含其他的信息：</p>
<p>比如品牌的官网，品牌的世界排名，品牌的市值等等；</p>
<p>如果我们直接在商品中去体现品牌相关的信息，会存在一些问题：</p>
<p>一方面，products表中应该表示的都是商品相关的数据，应该又另外一张表来表示brand的数据；</p>
<p>另一方面，多个商品使用的品牌是一致时，会存在大量的冗余数据；</p>
<p>所以，我们可以将所有的品牌数据，单独放到一张表中，创建一张品牌的表</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> <span class="token keyword">IF</span> <span class="token operator">NOT</span> <span class="token keyword">EXISTS</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span><span class="token punctuation">(</span>
id <span class="token keyword">INT</span> <span class="token keyword">PRIMARY</span> <span class="token keyword">KEY</span> <span class="token keyword">AUTO_INCREMENT</span><span class="token punctuation">,</span>
name <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">)</span> <span class="token operator">NOT</span> <span class="token boolean">NULL</span><span class="token punctuation">,</span>
website <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">100</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
worldRank <span class="token keyword">INT</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>插入模拟数据</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">INSERT</span> <span class="token keyword">INTO</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token punctuation">(</span>name<span class="token punctuation">,</span> website<span class="token punctuation">,</span> worldRank<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token string">'华为'</span><span class="token punctuation">,</span> <span class="token string">'www.huawei.com'</span><span class="token punctuation">,</span> <span class="token number">1</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">INSERT</span> <span class="token keyword">INTO</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token punctuation">(</span>name<span class="token punctuation">,</span> website<span class="token punctuation">,</span> worldRank<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token string">'小米'</span><span class="token punctuation">,</span> <span class="token string">'www.mi.com'</span><span class="token punctuation">,</span> <span class="token number">10</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">INSERT</span> <span class="token keyword">INTO</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token punctuation">(</span>name<span class="token punctuation">,</span> website<span class="token punctuation">,</span> worldRank<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token string">'苹果'</span><span class="token punctuation">,</span> <span class="token string">'www.apple.com'</span><span class="token punctuation">,</span> <span class="token number">5</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">INSERT</span> <span class="token keyword">INTO</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token punctuation">(</span>name<span class="token punctuation">,</span> website<span class="token punctuation">,</span> worldRank<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token string">'oppo'</span><span class="token punctuation">,</span> <span class="token string">'www.oppo.com'</span><span class="token punctuation">,</span> <span class="token number">15</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">INSERT</span> <span class="token keyword">INTO</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token punctuation">(</span>name<span class="token punctuation">,</span> website<span class="token punctuation">,</span> worldRank<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token string">'京东'</span><span class="token punctuation">,</span> <span class="token string">'www.jd.com'</span><span class="token punctuation">,</span> <span class="token number">3</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
<span class="token keyword">INSERT</span> <span class="token keyword">INTO</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token punctuation">(</span>name<span class="token punctuation">,</span> website<span class="token punctuation">,</span> worldRank<span class="token punctuation">)</span> <span class="token keyword">VALUES</span> <span class="token punctuation">(</span><span class="token string">'Google'</span><span class="token punctuation">,</span> <span class="token string">'www.google.com'</span><span class="token punctuation">,</span> <span class="token number">8</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h4 id="创建外键" tabindex="-1"><a class="header-anchor" href="#创建外键" aria-hidden="true">#</a> 创建外键</h4>
<p>将两张表联系起来，我们可以将products中的brand_id关联到brand中的id：</p>
<p>如果是创建表添加外键约束，我们需要在创建表的()最后添加如下语句；</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span>brand_id<span class="token punctuation">)</span> <span class="token keyword">REFERENCES</span> brand<span class="token punctuation">(</span>id<span class="token punctuation">)</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>如果是表已经创建好，额外添加外键：</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">ADD</span> <span class="token identifier"><span class="token punctuation">`</span>brand_id<span class="token punctuation">`</span></span> <span class="token keyword">INT</span><span class="token punctuation">;</span>
<span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">ADD</span> <span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span>brand_id<span class="token punctuation">)</span> <span class="token keyword">REFERENCES</span> brand<span class="token punctuation">(</span>id<span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><p>现在我们可以将products中的brand_id关联到brand中的id的值：</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">UPDATE</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">SET</span> <span class="token identifier"><span class="token punctuation">`</span>brand_id<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token number">1</span> <span class="token keyword">WHERE</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token string">'华为'</span><span class="token punctuation">;</span>
<span class="token keyword">UPDATE</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">SET</span> <span class="token identifier"><span class="token punctuation">`</span>brand_id<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token number">4</span> <span class="token keyword">WHERE</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token string">'OPPO'</span><span class="token punctuation">;</span>
<span class="token keyword">UPDATE</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">SET</span> <span class="token identifier"><span class="token punctuation">`</span>brand_id<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token number">3</span> <span class="token keyword">WHERE</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token string">'苹果'</span><span class="token punctuation">;</span>
<span class="token keyword">UPDATE</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">SET</span> <span class="token identifier"><span class="token punctuation">`</span>brand_id<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token number">2</span> <span class="token keyword">WHERE</span> <span class="token identifier"><span class="token punctuation">`</span>brand<span class="token punctuation">`</span></span> <span class="token operator">=</span> <span class="token string">'小米'</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h4 id="外键存在时更新和删除数据" tabindex="-1"><a class="header-anchor" href="#外键存在时更新和删除数据" aria-hidden="true">#</a> 外键存在时更新和删除数据</h4>
<p>先找到外键名</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">SHOW</span> <span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>删除外键</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">DROP</span> <span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> products_ibfk_1<span class="token punctuation">;</span> <span class="token comment">//外键名products_ibfk_1</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>重新设置</p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">ALTER</span> <span class="token keyword">TABLE</span> <span class="token identifier"><span class="token punctuation">`</span>products<span class="token punctuation">`</span></span> <span class="token keyword">ADD</span> <span class="token keyword">FOREIGN</span> <span class="token keyword">KEY</span> <span class="token punctuation">(</span>brand_id<span class="token punctuation">)</span> <span class="token keyword">REFERENCES</span> brand<span class="token punctuation">(</span>id<span class="token punctuation">)</span> 
<span class="token keyword">ON</span> <span class="token keyword">UPDATE</span> <span class="token keyword">CASCADE</span> 
<span class="token keyword">ON</span> <span class="token keyword">DELETE</span> <span class="token keyword">CASCADE</span><span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p><strong>CASCADE</strong>：当更新或删除某个记录时，会检查该记录是否有关联的外键记录，有的话：</p>
<p>✓ 更新：那么会更新对应的记录； ✓ 删除：那么关联的记录会被一起删除掉；</p>
<h3 id="多表查询" tabindex="-1"><a class="header-anchor" href="#多表查询" aria-hidden="true">#</a> 多表查询</h3>
</div></template>
