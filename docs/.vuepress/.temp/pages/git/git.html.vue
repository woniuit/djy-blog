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
</div></template>
