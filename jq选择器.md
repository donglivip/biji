###Welcome to use MarkDown
:first页面中的第一个标签
:last页面中的最后个标签
:first-chlid;兄弟元素中第一个
:last-chlid;兄弟元素中最后个
:nt-chlid()
siblings()兄弟元素
:eq()
:gt()第几个元素后面的所有元素
not(':eq(2)')除了第三个之外其他所有的;;;;过滤效果
filter(':eq(2)')只有第三个;;;筛选效果
div:has('a')包含a标签的div
a[title]设置了title属性的a标签
a[href^=www]以www开头的
a[href$=www]以www结尾的
a[href*=www]包含www的
a[href='www']值等于www的



size()类似于length
$('div').find('span')寻找div下的span
is(':checked')判断是否选中,返回boolean值$('input').is(':checked')
