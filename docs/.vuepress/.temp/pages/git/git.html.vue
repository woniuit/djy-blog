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
<ul>
<li>配置命令如下：</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code># your_name：名字或昵称
git config --global user.name 'your_name'
# your_email@domain.com：邮箱地址
git config --global user.email 'your_email@domain.com'
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><ul>
<li>想要查看 <code v-pre>config</code> 的配置，可使用如下命令：</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code># 查看当前仓库 config
git config --list --local
# 查看当前用户 config
git config --list --global
# 查看当前系统 config
git config --list --system
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><ul>
<li>
<p>除了设置 <code v-pre>--global</code>，还可以设置 <code v-pre>--local</code> 和 <code v-pre>--system</code>，这三个都有什么区别呢？</p>
</li>
<li>
<p><code v-pre>--local</code>：只对某个仓库有效。</p>
</li>
<li>
<p><code v-pre>--global</code>：对当前用户（比如 windows 的 User 环境）所有仓库有效。</p>
</li>
<li>
<p><code v-pre>--system</code>：对系统所有登录的用户（比如 windows 的 System 环境）有效，此配置不常用。</p>
</li>
</ul>
<h3 id="获取git仓库" tabindex="-1"><a class="header-anchor" href="#获取git仓库" aria-hidden="true">#</a> 获取git仓库</h3>
<ul>
<li>方式一：</li>
</ul>
<div class="language-git ext-git line-numbers-mode"><pre v-pre class="language-git"><code>git init //初始化本地git仓库
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><ul>
<li>方式二：</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git clone //克隆远程仓库
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="检测文件的状态" tabindex="-1"><a class="header-anchor" href="#检测文件的状态" aria-hidden="true">#</a> 检测文件的状态</h3>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git status
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="文件添加到暂存区" tabindex="-1"><a class="header-anchor" href="#文件添加到暂存区" aria-hidden="true">#</a> 文件添加到暂存区</h3>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git add .
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="文件更新提交" tabindex="-1"><a class="header-anchor" href="#文件更新提交" aria-hidden="true">#</a> 文件更新提交</h3>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git commit -m '提交信息'
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="查看提交的历史" tabindex="-1"><a class="header-anchor" href="#查看提交的历史" aria-hidden="true">#</a> 查看提交的历史</h3>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git log
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><ul>
<li>如果提交信息过多，可以按<code v-pre>enter</code>键查看更多,按<code v-pre>Q</code>键可以退出</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git log --pretty=oneline   //提交信息显示在一行
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git reflog  //可以查看更多更全的提交历史信息（回退前后）
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><h3 id="commit合并" tabindex="-1"><a class="header-anchor" href="#commit合并" aria-hidden="true">#</a> commit合并</h3>
<ul>
<li>对比两个commit</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git diff 0c3cebb e2e1eb1
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><ul>
<li>修改commit的msg</li>
</ul>
<p>确保此分支并未合到主分支，才进行 commit 的 message 修改，否则会影响团队中的其他人的开发。</p>
<ul>
<li>
<p>修改最新 commit 的 message</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git commit --amend
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>执行上面的命令，会进入vim编辑器，输入<code v-pre>i</code>编辑，然后编辑commit信息，按esc保存，然后输入<code v-pre>:wq</code>退出。</p>
</li>
<li>
<p>修改老旧的commit</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git rebase -i 69946775404982fa60e1e23cff13fd801e8a4ad9
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><p>执行上面的命令，会进入vim编辑器，内容大概如下</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>pick 0279a2c add README.md
pick 7a48866 update

# Rebase 6994677..7a48866 onto 6994677 (2 commands)
#
# Commands:
# p, pick &lt;commit> = use commit
# r, reword &lt;commit> = use commit, but edit the commit message
# e, edit &lt;commit> = use commit, but stop for amending
# s, squash &lt;commit> = use commit, but meld into previous commit
# f, fixup [-C | -c] &lt;commit> = like "squash" but keep only the previous
#                    commit's log message, unless -C is used, in which case
#                    keep only this commit's message; -c is same as -C but
#                    opens the editor
# x, exec &lt;command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop &lt;commit> = remove commit
# l, label &lt;label> = label current HEAD with a name
# t, reset &lt;label> = reset HEAD to a label
# m, merge [-C &lt;commit> | -c &lt;commit>] &lt;label> [# &lt;oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified); use -c &lt;commit> to reword the commit message
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>将第一行的 <code v-pre>pick</code> 改为 <code v-pre>r</code> 或 <code v-pre>reword</code> 后，保存退出 vi 编辑器即可。</p>
<p>接着会打开另一个 vi 编辑器，让你编辑新的 message。如下：</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>add README.md

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Mon Apr 25 13:07:55 2022 +0800
#
# interactive rebase in progress; onto 6994677
# Last command done (1 command done):
#    reword 0279a2c add README.md
# Next command to do (1 remaining command):
#    pick 7a48866 update
# You are currently editing a commit while rebasing branch 'master' on '6994677'.
#
# Changes to be committed:
#       new file:   README.md
#
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>此处将 <code v-pre>add README.md</code> 修改为 <code v-pre>feat: add README.md</code> 后保存退出，使用 <code v-pre>git log</code> 查看是否修改成功。</p>
<p>退出git rebase</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git rebase --abort
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div></li>
<li>
<p>把连续的多个 commit 整理成一个</p>
<p>先<code v-pre>git log</code>查看提交的记录,如下</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>commit 50650ab1dc900a57e223504a53aa5d1963432f5b (HEAD -> devslop, origin/devslop)
Author: dengjunyu &lt;dengjunyu.Software.chinasofti>
Date:   Tue Jan 10 11:19:57 2023 +0800
noop

    333

commit 9f7968081d07a79aaab7b84eee48bc607d98bc90
Author: dengjunyu &lt;dengjunyu.Software.chinasofti>
Date:   Tue Jan 10 11:19:40 2023 +0800

    222

commit 4c9feff732331adf290a5de690ffd9207e3f625a
Author: dengjunyu &lt;dengjunyu.Software.chinasofti>
Date:   Tue Jan 10 11:15:30 2023 +0800

    1111

commit e2841f359db2dd04a6d2dbb27dbcca6681ce340f
Author: dengjunyu &lt;dengjunyu.Software.chinasofti>
Date:   Mon Jan 9 17:46:27 2023 +0800

    999
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>这个仓库，一共有 4 条 commit，现在我们把 1、2、3 条合为一条。跟修改老旧 commit 的 message 一样，<code v-pre>git rebase -i [commit]</code> 的 <code v-pre>[commit]</code> 需要是第 4 条的 commit 才行<code v-pre>git rebase -i e2841f359db2dd04a6d2dbb27dbcca6681ce340f </code>，执行成功后，如下：</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>pick 4c9feff 1111
pick 9f79680 222
pick 50650ab 333

# Rebase e2841f3..50650ab onto e2841f3 (3 commands)
#
# Commands:
# p, pick &lt;commit> = use commit
# r, reword &lt;commit> = use commit, but edit the commit message
# e, edit &lt;commit> = use commit, but stop for amending
# s, squash &lt;commit> = use commit, but meld into previous commit
# f, fixup [-C | -c] &lt;commit> = like "squash" but keep only the previous
#                    commit's log message, unless -C is used, in which case
#                    keep only this commit's message; -c is same as -C but
#                    opens the editor
# x, exec &lt;command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop &lt;commit> = remove commit
# l, label &lt;label> = label current HEAD with a name
# t, reset &lt;label> = reset HEAD to a label
# m, merge [-C &lt;commit> | -c &lt;commit>] &lt;label> [# &lt;oneline>]
#         create a merge commit using the original merge commit's
#         message (or the oneline, if no original merge commit was
#         specified); use -c &lt;commit> to reword the commit message
# u, update-ref &lt;ref> = track a placeholder for the &lt;ref> to be updated
#                       to this position in the new commits. The &lt;ref> is
#                       updated at the end of the rebase
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
C:/Users/dengj/Desktop/git/.git/rebase-merge/git-rebase-todo [unix] (11:33 10/01/2023)                                 1,1 全部
"C:/Users/dengj/Desktop/git/.git/rebase-merge/git-rebase-todo" [unix] 34L, 1533B     
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>把上面第二行和第三行的pick改成<code v-pre>s</code>，意味着，把二和三的commit合并到第一行，然后esc保存退出，会进入一个新的编辑，然后就编辑第一条commit的信息。再退出git log就可以看到是否成功了。</p>
<ul>
<li>把间隔的几个 commit 整理成一个 (没有实践过)</li>
</ul>
<p>想要将间隔的几个 commit 整理成一个，跟上边【把连续的多个 commit 整理成一个】的方法类似，操作稍微有些许不同。还是老样子，先看看当前分支的 log，如下：</p>
<p>bash</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>$ git log
commit 66c1c4f331c67f6f282126883df6e800a70bbe1c (HEAD -> master, origin/master)
Merge: 9e007cc 02e2887
Author: SaltedFish &lt;1041288269@qq.com>
Date:   Wed May 11 16:55:35 2022 +0800

    fix

commit 9e007cc9bd94810601bcef5ed167484187e39b9e
Author: SaltedFish &lt;1041288269@qq.com>
Date:   Wed May 11 16:54:53 2022 +0800

    feat: update title to AAAAA

commit c2af50bc750d5260d31ed083c9315f83b059f71e
Author: SaltedFish &lt;1041288269@qq.com>
Date:   Wed May 11 16:46:37 2022 +0800

    feat: test1

commit 02e288782ca80fe45ccc1c3ed1bb3ba9f7ce2bb9
Author: SaltedFish &lt;1041288269@qq.com>
Date:   Tue Apr 26 13:36:57 2022 +0800

    update

commit 3372452c886bd877d4ba07a67ef6bb70ba6bee56
Author: SaltedFish &lt;1041288269@qq.com>
Date:   Mon Apr 25 13:07:55 2022 +0800

    add README.md

commit 69946775404982fa60e1e23cff13fd801e8a4ad9
Author: SaltedFish &lt;1041288269@qq.com>
Date:   Mon Apr 25 13:06:45 2022 +0800

    init
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>现在整个分支就有 6 个 commit，这次将第 4 条和第 6 条 commit 进行合并，执行 <code v-pre>git rebase -i [commit]</code> 命令，由于第 6 条已经是最后一条，<code v-pre>[commit]</code> 就先使用最后一条的 commit，看看执行后的结果。如下：</p>
<p>bash</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>pick c2af50b feat: test1
pick 9e007cc feat: update title to AAAAA
pick 3372452 add README.md
pick 02e2887 update

# Rebase 6994677..66c1c4f onto 6994677 (4 commands)
#
# Commands:
# p, pick &lt;commit> = use commit
# r, reword &lt;commit> = use commit, but edit the commit message
# e, edit &lt;commit> = use commit, but stop for amending
# s, squash &lt;commit> = use commit, but meld into previous commit
# f, fixup [-C | -c] &lt;commit> = like "squash" but keep only the previous
#                    commit's log message, unless -C is used, in which case
#                    keep only this commit's message; -c is same as -C but
#                    opens the editor
# x, exec &lt;command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop &lt;commit> = remove commit
# l, label &lt;label> = label current HEAD with a name
# t, reset &lt;label> = reset HEAD to a label
# m, merge [-C &lt;commit> | -c &lt;commit>] &lt;label> [# &lt;oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified); use -c &lt;commit> to reword the commit message
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>会发现，并没有下边这条 commit：</p>
<p>bash</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>commit 69946775404982fa60e1e23cff13fd801e8a4ad9
Author: SaltedFish &lt;1041288269@qq.com>
Date:   Mon Apr 25 13:06:45 2022 +0800

    init
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>这时候就需要我们自己手动添加进去了，修改之后如下：</p>
<p>bash</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>pick 6994677
s 02e2887 update
pick c2af50b feat: test1
pick 9e007cc feat: update title to AAAAA
pick 3372452 add README.md

# Rebase 6994677..66c1c4f onto 6994677 (4 commands)
#
# Commands:
# p, pick &lt;commit> = use commit
# r, reword &lt;commit> = use commit, but edit the commit message
# e, edit &lt;commit> = use commit, but stop for amending
# s, squash &lt;commit> = use commit, but meld into previous commit
# f, fixup [-C | -c] &lt;commit> = like "squash" but keep only the previous
#                    commit's log message, unless -C is used, in which case
#                    keep only this commit's message; -c is same as -C but
#                    opens the editor
# x, exec &lt;command> = run command (the rest of the line) using shell
# b, break = stop here (continue rebase later with 'git rebase --continue')
# d, drop &lt;commit> = remove commit
# l, label &lt;label> = label current HEAD with a name
# t, reset &lt;label> = reset HEAD to a label
# m, merge [-C &lt;commit> | -c &lt;commit>] &lt;label> [# &lt;oneline>]
# .       create a merge commit using the original merge commit's
# .       message (or the oneline, if no original merge commit was
# .       specified); use -c &lt;commit> to reword the commit message
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>在第一行添加了 <code v-pre>pick 6994677</code>，这条就是缺少的那条 commit，由于需要跨行合并，我们把原本的 <code v-pre>pick 02e2887 update</code> 先修改成 <code v-pre>s 02e2887 update</code> 并移动到了 <code v-pre>pick 6994677</code> 后边，修改完成后，保存退出。</p>
<p>保存后，并没有跳到我们预想的编辑 message 部分，而是弹出了如下提示：</p>
<p>bash</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>$ git rebase -i 69946775404982fa60e1e23cff13fd801e8a4ad9
interactive rebase in progress; onto 6994677
Last command done (1 command done):
   pick 6994677
Next commands to do (2 remaining commands):
   squash 2b4b4a6 feat: test2
   pick c2af50b feat: test1
  (use "git rebase --edit-todo" to view and edit)
You are currently rebasing branch 'master' on '6994677'.
  (all conflicts fixed: run "git rebase --continue")

nothing to commit, working tree clean
The previous cherry-pick is now empty, possibly due to conflict resolution.
If you wish to commit it anyway, use:

    git commit --allow-empty

Otherwise, please use 'git rebase --skip'
Could not apply 6994677...
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>执行一下 <code v-pre>git status</code> 当前工作目录的状态，如下：</p>
<p>bash</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>$ git status
interactive rebase in progress; onto 6994677
Last command done (1 command done):
   pick 6994677
Next commands to do (4 remaining commands):
   squash 02e2887 update
   pick c2af50b feat: test1
  (use "git rebase --edit-todo" to view and edit)
You are currently rebasing branch 'master' on '6994677'.
  (all conflicts fixed: run "git rebase --continue")

nothing to commit, working tree clean
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>最后一行提示，工作目录 tree 是干净的，这样，只需要根据提示，使用 <code v-pre>git rebase --continue</code> 就可以进入到编辑 message 的步骤。如下：</p>
<p>bash</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code># This is a combination of 2 commits.
# This is the 1st commit message:

init

# This is the commit message #2:

update

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Mon Apr 25 13:06:45 2022 +0800
#
# interactive rebase in progress; onto 6994677
# Last commands done (2 commands done):
#    pick 6994677
#    squash 02e2887 update
# Next commands to do (3 remaining commands):
#    pick c2af50b feat: test1
#    pick 9e007cc feat: update title to AAAAA
# You are currently rebasing branch 'master' on '6994677'.
#
#
# Initial commit
#
# Changes to be committed:
#       new file:   decode.js
#       new file:   index.html
#       new file:   index.js
#       new file:   pako.min.js
#
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>修改一下 message，如下：</p>
<p>bash</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code># This is a combination of 2 commits.
feat: new AAAAA
# This is the 1st commit message:

init

# This is the commit message #2:

update

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# Date:      Mon Apr 25 13:06:45 2022 +0800
#
# interactive rebase in progress; onto 6994677
# Last commands done (2 commands done):
#    pick 6994677
#    squash 02e2887 update
# Next commands to do (3 remaining commands):
#    pick c2af50b feat: test1
#    pick 9e007cc feat: update title to AAAAA
# You are currently rebasing branch 'master' on '6994677'.
#
#
# Initial commit
#
# Changes to be committed:
#       new file:   decode.js
#       new file:   index.html
#       new file:   index.js
#       new file:   pako.min.js
#
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>修改完成后，保存退出，正常会输出如下信息：</p>
<p>bash</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>$ git rebase --continue
[detached HEAD 07699cf] feat: test1
 1 file changed, 1 insertion(+), 1 deletion(-)
Successfully rebased and updated refs/heads/master.
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>使用 <code v-pre>git log</code> 查看是否已经合并完成，如下：</p>
<p>bash</p>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>$ git log
commit 48a6bafd20501c2fabad3a22c217da405580067f (HEAD -> master)
Author: SaltedFish &lt;1041288269@qq.com>
Date:   Mon Apr 25 13:07:55 2022 +0800

    add README.md

commit f0f4b3376eaa8a34438239a7eadf319784d0b303
Author: SaltedFish &lt;1041288269@qq.com>
Date:   Wed May 11 16:54:53 2022 +0800

    feat: update title to AAAAA

commit 07699cf7d647d78f71de58e9386c834e2b99bcbe
Author: SaltedFish &lt;1041288269@qq.com>
Date:   Wed May 11 16:46:37 2022 +0800

    feat: test1

commit c732a178b83e8feda16790c8912b5da19fb8242b
Author: SaltedFish &lt;1041288269@qq.com>
Date:   Mon Apr 25 13:06:45 2022 +0800

    feat: new AAAAA

    init

    update
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><p>可以看到，message 为 <code v-pre>init</code> 和 <code v-pre>update</code> 的 commit 已经合并为一条。</p>
<p><strong>注意点：</strong></p>
<ol>
<li>如果在 <code v-pre>git rebase --continue</code> 的时候出现代码冲突，需要先解决完冲突，执行 <code v-pre>git add .</code> 后，再次执行 <code v-pre>git rebase --continue</code>，会弹出编辑 message 的操作，什么也不用做，保存退出即可。</li>
<li>使用 <code v-pre>git rebase -i [commit]</code> 时如果为最后一条，可以使用 <code v-pre>git rebase -i --root</code> 来替代，这样就可以省区手动添加最后一条 commit 的步骤。</li>
</ol>
</li>
</ul>
<h3 id="版本回退" tabindex="-1"><a class="header-anchor" href="#版本回退" aria-hidden="true">#</a> 版本回退</h3>
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
<ul>
<li>查看是否有连接远程仓库</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git remote  //如果出现origin就是连接了
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git remote -v //查看连接的具体仓库
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><ul>
<li>连接远程仓库</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git init //先初始化仓库
git remote add origin 仓库地址
git remote //查看是否连接成功
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div><div class="line-number"></div></div></div><ul>
<li>移除远程连接</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git remote remove origin
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><ul>
<li>本地分支的上游分支（跟踪分支）</li>
</ul>
<p>本地仓库和远程仓库连接之后，执行git pull拉取远程分支会报如下的错误</p>
<p><img src="/23.png" alt="23"></p>
<p>原因是因为当前分支没有和远程的origin/master分支进行跟踪</p>
<ul>
<li>解决1</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git pull origin master
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><ul>
<li>解决2</li>
</ul>
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
<ul>
<li>创建分支</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git branch 分支名
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><ul>
<li>创建分支并切换到新分支</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git checkout -b 分支名
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><ul>
<li>切换分支</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git checkout 分支名  //可以切换到本地分支也可以直接切换到远程分支
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><ul>
<li>合并分支</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git merge 合并的分支名
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div></div></div><ul>
<li>查看分支</li>
</ul>
<div class="language-text ext-text line-numbers-mode"><pre v-pre class="language-text"><code>git branch //查看分支
git branch -v //查看分支，并可以看到最后一次提交的commit
</code></pre><div class="line-numbers" aria-hidden="true"><div class="line-number"></div><div class="line-number"></div></div></div><ul>
<li>删除分支</li>
</ul>
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
<h3 id="rebase" tabindex="-1"><a class="header-anchor" href="#rebase" aria-hidden="true">#</a> rebase</h3>
<p>和marge差不多，历史记录不同</p>
<h3 id="git-flow" tabindex="-1"><a class="header-anchor" href="#git-flow" aria-hidden="true">#</a> git flow</h3>
<p><img src="https://img-blog.csdnimg.cn/20210402174827663.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjY3NDYxMA==,size_16,color_FFFFFF,t_70" alt="在这里插入图片描述"></p>
</div></template>
