---
layout: post
title: "linux crontab"
date: 2012-03-01 10:15
comments: true
categories: linux
---

每个系统有一个全局 crontab 文件, 位于 /etc/crontab.

每个用户可以有自己独立的 crontab 文件, 位于 /var/spool/cron/crontabs , 但该文件并不设计为手动编辑的, 正确的方法是使用 crontab -e 来编辑自己的 crontab 文件.

编辑自己用户的 `crontab` 文件

{% codeblock lang:sh %}
	crontab -e
{% endcodeblock %}

格式是:
{% codeblock lang:sh %}
	# m h dom mon dow command
  	  * *  *   *   *  curl http://yiriji.com/admin/cron`
{% endcodeblock %}
* m, 分钟
* h, 小时
* dom, day of month, 日期
* mon, month, 月份
* dow, day of week, 星期

和全局的 crontab 不同的是, 没有用户名这一列

###Ubuntu中的全局crontab文件示范:
{% codeblock lang:sh %}
	# m h dom mon dow user  command

    # 每天每个小时的第17分执行 /etc/cron.hourly 文件下的所有可执行程序或脚本
	17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly

	# 每天6点25分执行
	25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

	# 每个星期天的6点47分执行
	47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )

	# 每月1号6点52分执行
	52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
{% endcodeblock %}
run-parts 的意思就是执行该文件夹下所有可执行程序或脚本.

> 本该淡淡然~~~
