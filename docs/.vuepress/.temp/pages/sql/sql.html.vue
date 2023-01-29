<template><div><h1 id="sql" tabindex="-1"><a class="header-anchor" href="#sql" aria-hidden="true">#</a> sql</h1>
<h2 id="mongodb" tabindex="-1"><a class="header-anchor" href="#mongodb" aria-hidden="true">#</a> MongoDB</h2>
<p><strong><a href="https://yangyongli.blog.csdn.net/article/details/113917773?spm=1001.2101.3001.6650.1&amp;utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-113917773-blog-114709588.t5_layer_eslanding_A_4&amp;depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-113917773-blog-114709588.t5_layer_eslanding_A_4&amp;utm_relevant_index=2" target="_blank" rel="noopener noreferrer">安装<ExternalLinkIcon/></a></strong></p>
<h3 id="常用的语句" tabindex="-1"><a class="header-anchor" href="#常用的语句" aria-hidden="true">#</a> <strong>常用的语句</strong></h3>
<p><strong>查看当前数据库列表</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>show dbs
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查看当前操作的数据库</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>切换数据库（如果没有这个数据库 会 创建数据库）</strong></p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>use 数据库名称
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>如果真的想把这个数据库创建成功，那么必须插入一个数据。 数据库中不能直接插入数据，只能往<a href="https://so.csdn.net/so/search?q=%E9%9B%86%E5%90%88&amp;spm=1001.2101.3001.7020" target="_blank" rel="noopener noreferrer">集合<ExternalLinkIcon/></a>(collections)中插入数据。
下面命令表示给 itying 数据库的 user 表中插入数据。</p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.user.insert({&quot;name&quot;:&quot;xiaoming&quot;});
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>显示当前的数据集合</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>show collections
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>删除指定的集合 删除表</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.user.drop();
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>删除当前所在的数据库</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.dropDatabase();
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>插入（增加）数据</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.表名.insert({&quot;name&quot;:&quot;zhangsan&quot;，&quot;age&quot;:20});
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询所有记录</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.user.find();
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 age = 22 的记录</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.user.find({&quot;age&quot;: 22});
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 age &gt; 22 的记录</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.user.find({&quot;age&quot;: {$gt: 22}});
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 age &lt; 22 的记录</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.user.find({&quot;age&quot;: {$lt: 22}});
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 age &gt;= 25 的记录</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.user.find({&quot;age&quot;: {$gte: 25}});
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 age &lt;= 25 的记录</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.user.find({&quot;age&quot;: {$lte: 25}});
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 age &gt;= 23 并且 age &lt;= 26</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.user.find({&quot;age&quot;: {$gte: 23, $lte: 26}});
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 name 中包含 mongo 的数据 模糊查询用于搜索</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.user.find({&quot;name&quot;: /mongo/});
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 name 中以 mongo 开头的</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.user.find({&quot;name&quot;: /^mongo/});
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>查询 name 中以 mongo 结尾的</strong></p>
<div class="language-mysql ext-mysql line-numbers-mode"><pre v-pre class="language-mysql"><code>db.user.find({&quot;name&quot;: /mongo$/});
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
<h3 id="gut工具" tabindex="-1"><a class="header-anchor" href="#gut工具" aria-hidden="true">#</a> Gut工具</h3>
<p>Navicat</p>
<h3 id="mysql的操作" tabindex="-1"><a class="header-anchor" href="#mysql的操作" aria-hidden="true">#</a> mysql的操作</h3>
<p><strong>查看当前数据库</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment">#查看所有的数据库</span>
<span class="token keyword">SHOW</span> <span class="token keyword">DATABASES</span>

<span class="token comment"># 使用某一个数据</span>
<span class="token keyword">USE</span> coderhub<span class="token punctuation">(</span>数据库名称<span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token comment"># 查看当前正在使用的数据库</span>
<span class="token keyword">SELECT</span> <span class="token keyword">DATABASE</span><span class="token punctuation">(</span><span class="token punctuation">)</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p><strong>创建新的数据库</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 创建数据库语句</span>
<span class="token keyword">CREATE</span> <span class="token keyword">DATABASE</span> <span class="token keyword">IF</span> <span class="token operator">NOT</span> <span class="token keyword">EXISTS</span> bilibili<span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><p><strong>删除数据库</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 删除数据库</span>
<span class="token keyword">DROP</span> <span class="token keyword">DATABASE</span> <span class="token keyword">IF</span> <span class="token keyword">EXIT</span> bilibili<span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><p><strong>修改数据库</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 修改数据库的字符集和排序规则</span>
<span class="token keyword">ALTER</span> <span class="token keyword">DATABASE</span> bilibili <span class="token keyword">CHARACTER</span> <span class="token keyword">SET</span> <span class="token operator">=</span> utf8 <span class="token keyword">COLLATE</span> <span class="token operator">=</span> utf8_unicode_ci<span class="token punctuation">;</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="数据库表的操作" tabindex="-1"><a class="header-anchor" href="#数据库表的操作" aria-hidden="true">#</a> 数据库表的操作</h3>
<p><strong>查看数据表</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token comment"># 查看所有的数据表</span>
<span class="token keyword">SHOW</span> <span class="token keyword">TABLES</span><span class="token punctuation">;</span>
<span class="token comment"># 查看某一个表结构</span>
<span class="token keyword">DESC</span> <span class="token keyword">user</span>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p><strong>创建数据表</strong></p>
<div class="language-sql ext-sql line-numbers-mode"><pre v-pre class="language-sql"><code><span class="token keyword">CREATE</span> <span class="token keyword">TABLE</span> <span class="token keyword">IF</span> <span class="token operator">NOT</span> <span class="token keyword">EXISTS</span> <span class="token identifier"><span class="token punctuation">`</span>users<span class="token punctuation">`</span></span><span class="token punctuation">(</span>
name <span class="token keyword">VARCHAR</span><span class="token punctuation">(</span><span class="token number">20</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
age <span class="token keyword">INT</span><span class="token punctuation">,</span>
height <span class="token keyword">DOUBLE</span>
<span class="token punctuation">)</span><span class="token punctuation">;</span>

</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div></div></template>
