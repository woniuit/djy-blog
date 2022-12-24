<template><div><h2 id="集中式版本控制" tabindex="-1"><a class="header-anchor" href="#集中式版本控制" aria-hidden="true">#</a> 集中式版本控制</h2>
<p>CVS和SVN都是是属于集中式版本控制系统</p>
<p><strong>特点</strong>：</p>
<ul>
<li>单一的集中管理的服务器，保存所有文件的修订版本</li>
<li>协同开发人员通过客户端连接到这台服务器，取出最新的文件或者提交更新</li>
</ul>
<p><strong>核心问题</strong>：</p>
<ul>
<li>中央服务器不能出现故障</li>
<li>如果宕机一小时，那么在这一小时内，谁都无法提 交更新，也就无法协同工作</li>
<li>如果中心数据库所在的磁盘发生损坏，又没有做恰 当备份，毫无疑问你将丢失所有数据</li>
</ul>
<h2 id="分布式版本控制" tabindex="-1"><a class="header-anchor" href="#分布式版本控制" aria-hidden="true">#</a> 分布式版本控制</h2>
<p>Git是属于分布式版本控制系统</p>
<p><strong>特点</strong></p>
<ul>
<li>客户端并不只提取最新版本的文件快照， 而是<strong>把代码仓库完整地镜像下 来，包括完整的历史记录</strong>；</li>
<li>任何一处协同工作用的服务器发生故障，事后都可以用任何 一个镜像出来的本地仓库恢复</li>
<li>每一次的克隆操作，实际上都是一次对代码仓库的完整备份</li>
</ul>
<h2 id="git常用的操作" tabindex="-1"><a class="header-anchor" href="#git常用的操作" aria-hidden="true">#</a> git常用的操作</h2>
<h3 id="获取git仓库" tabindex="-1"><a class="header-anchor" href="#获取git仓库" aria-hidden="true">#</a> 获取git仓库</h3>
<p>方式一：</p>
<div class="language-git ext-git line-numbers-mode"><pre v-pre class="language-git"><code>git init //初始化本地git仓库
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>方式二：</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git clone //克隆远程仓库
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="检测文件的状态" tabindex="-1"><a class="header-anchor" href="#检测文件的状态" aria-hidden="true">#</a> 检测文件的状态</h3>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git status
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="文件添加到暂存区" tabindex="-1"><a class="header-anchor" href="#文件添加到暂存区" aria-hidden="true">#</a> 文件添加到暂存区</h3>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git add .
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="文件更新提交" tabindex="-1"><a class="header-anchor" href="#文件更新提交" aria-hidden="true">#</a> 文件更新提交</h3>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git commit -m '提交信息'
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="查看提交的历史" tabindex="-1"><a class="header-anchor" href="#查看提交的历史" aria-hidden="true">#</a> 查看提交的历史</h3>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git log
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>如果提交信息过多，可以按<code v-pre>enter</code>键查看更多,按<code v-pre>Q</code>键可以退出</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git log --pretty=oneline   //提交信息显示在一行
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git reflog  //可以查看更多更全的提交历史信息（回退前后）
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="版本回退" tabindex="-1"><a class="header-anchor" href="#版本回退" aria-hidden="true">#</a> 版本回退</h3>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git reset
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git reset --hard HEAD^  //回退到上个版本
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git reset --hard HEAD^^ //回退到上上版本
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git reset --hard HEAD~1000 //上1000个版本
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git reset --hard 1234 //回退到指定版本
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div></div></template>
