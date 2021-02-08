# Words

一个Typecho的简单碎语插件

## Instructions

### 模板输出

在php页面中使用`Words_Plugin::render()`可直接调用预设模板样式输出碎语分页

*预设：* 复制template目录下的words.php到当前使用的主题目录下，后台**独立页面**新建页面自定义模板选择**心情碎语**

### 方法介绍

单独获取碎语内容`$words = Typecho_Widget::widget('Words_Action')->getWords()`（默认参数 $type='page', $pageSize=10）
> $type 获取模式
>
> * 'page'按$pageSize大小获取分页，返回数组：键'words'碎语条目数组；键'nav'分页盒，可用`$words['nav']->render(_t('&laquo;'), _t('&raquo;'))`输出
> * 'latest'最近一条碎语内容
> * 'single'按请求值获取一条碎语内容
> * 'all'全部碎语条目

单独获取评论内容`$comments = Typecho_Widget::widget('Words_Action')->getComments()`(默认参数 $type='page', $wid=NULL, $cid=NULL, $pageSize=10)
> $type 获取模式
>
> * 'page'按$pageSize大小获取分页，返回数组：键'comments'评论条目数组；键'nav'分页盒，可用`$comments['nav']->render(_t('&laquo;'), _t('&raquo;'))`输出
> * 'related'获取$wid代表碎语条目的所有评论
> * 'single'按$cid值获取一条评论内容
> * 'all'全部评论条目

`Typecho_Plugin::factory('Words_Action')->finishWord`（传入参数：array('created' => 创建时间, 'expression' => 表情图片名, 'content' => 碎语内容)）

`Typecho_Plugin::factory('Words_Action')->finishComment`（传入参数：array('wid' => 碎语id, 'created' => 创建时间, 'author' => 评论者, 'mail' => 邮箱, 'url' => 网站, 'ip' => IP, 'agent' => 平台, 'content' => 评论内容, 'parent' => 回复的评论id)）

`Typecho_Plugin::factory('Words_Action')->writeOption`（传入参数：class Words_Action）
