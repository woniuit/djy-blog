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
<h3 id="git配置" tabindex="-1"><a class="header-anchor" href="#git配置" aria-hidden="true">#</a> git配置</h3>
<p>Git 安装完成后，需配置代码提交人员的名字（昵称）和联系邮箱，配置成功后，之后提交代码修改时，会记录是谁修改了对应的代码，可以更好的管理和 Code Review。</p>
<p>配置命令如下：</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code># your_name：名字或昵称
git config --global user.name 'your_name'
# your_email@domain.com：邮箱地址
git config --global user.email 'your_email@domain.com'
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>想要查看 <code v-pre>config</code> 的配置，可使用如下命令：</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code># 查看当前仓库 config
git config --list --local
# 查看当前用户 config
git config --list --global
# 查看当前系统 config
git config --list --system
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>除了设置 <code v-pre>--global</code>，还可以设置 <code v-pre>--local</code> 和 <code v-pre>--system</code>，这三个都有什么区别呢？</p>
<ul>
<li><code v-pre>--local</code>：只对某个仓库有效。</li>
<li><code v-pre>--global</code>：对当前用户（比如 windows 的 User 环境）所有仓库有效。</li>
<li><code v-pre>--system</code>：对系统所有登录的用户（比如 windows 的 System 环境）有效，此配置不常用。</li>
</ul>
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
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="远程仓库验证-ssh密钥" tabindex="-1"><a class="header-anchor" href="#远程仓库验证-ssh密钥" aria-hidden="true">#</a> 远程仓库验证-SSH密钥</h3>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>ssh-keygen -t ed25519 -C “your email" //找到自己的密钥
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><img src="/21.png" alt="20"></p>
<p>然后去gitLab这样的远程仓库，点击设置，ssh，添加上自己的密钥</p>
<h3 id="本地连接远程仓库" tabindex="-1"><a class="header-anchor" href="#本地连接远程仓库" aria-hidden="true">#</a> 本地连接远程仓库</h3>
<p><strong>查看是否有连接远程仓库</strong></p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git remote  //如果出现origin就是连接了
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git remote -v //查看连接的具体仓库
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>连接远程仓库</strong></p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git init //先初始化仓库
git remote add origin 仓库地址
git remote //查看是否连接成功
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p><strong>移除远程连接</strong></p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git remote remove origin
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p><strong>本地分支的上游分支（跟踪分支）</strong></p>
<p>本地仓库和远程仓库连接之后，执行git pull拉取远程分支会报如下的错误</p>
<p><img src="/23.png" alt="23"></p>
<p>原因是因为当前分支没有和远程的origin/master分支进行跟踪</p>
<p>解决1</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git pull origin master
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>解决2</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git branch --set-upstream-to=origin/master
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="远程仓库的交互" tabindex="-1"><a class="header-anchor" href="#远程仓库的交互" aria-hidden="true">#</a> 远程仓库的交互</h3>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git add .
git commit -m 'XX'
git pull
git push
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><h3 id="tag标签" tabindex="-1"><a class="header-anchor" href="#tag标签" aria-hidden="true">#</a> tag标签</h3>
<p>对于重大的版本我们常常会打上一个标签，以表示它的重要性：</p>
<ul>
<li>
<p>Git 可以给仓库历史中的某一个提交打上标签；</p>
</li>
<li>
<p>比较有代表性的是人们会使用这个功能来标记发布结点（ v1.0 、 v2.0 等等）；</p>
</li>
</ul>
<p>创建标签</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git tag v1.0 //方式1
git tag -a v1.0 -m '附属信息' //方式2
git tag //查看tag
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>把本地的git标签推到远程</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git push origin v1.0
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>删除本地tag</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git tag -d v1.0
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>删除远程tag</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git push origin –delete &lt;tagname>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>检出tag</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git checkout &lt;tagname>
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="分支" tabindex="-1"><a class="header-anchor" href="#分支" aria-hidden="true">#</a> 分支</h3>
<p>创建分支</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git branch 分支名
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>创建分支并切换到新分支</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git checkout -b 分支名
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>切换分支</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git checkout 分支名
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>合并分支</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git merge 合并的分支名
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>查看分支</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git branch //查看分支
git branch -v //查看分支，并可以看到最后一次提交的commit
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><p>删除分支</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git branch –d hotfix # 删除当前分支
git branch –D hotfix # 强制删除某一个分支
git push origin --delete &lt;branch> //删除远程分支
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>为什么需要用到分支</p>
<p>让我们来看一个简单的分支新建与分支合并的例子，实际工作中你可能会用到类似的工作流。</p>
<ul>
<li>开发某个项目，在默认分支master上进行开发；</li>
<li>实现项目的功能需求，不断提交；</li>
<li>并且在一个大的版本完成时，发布版本，打上一个tag v1.0.0；</li>
</ul>
<p>继续开发后续的新功能，正在此时，你突然接到一个电话说有个很严重的问题需要紧急修补， 你将按照如下方式来处理</p>
<ul>
<li>切换到tag v1.0.0的版本，并且创建一个分支hotfix；</li>
</ul>
</div></template>
