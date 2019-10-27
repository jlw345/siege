# siege
Siege是一款开源的压力测试工具，设计用于评估WEB应用在压力下的承受能力。可以根据配置对一个WEB站点进行多用户的并发访问，记录每个用户所有请求过程的相应时间，并在一定数量的并发访问下重复进行。siege可以从您选择的预置列表中请求随机的URL。所以siege可用于仿真用户请求负载，而ab则不能。但不要使用siege来执行最高性能基准调校测试，这方面ab就准确很多。

假如说你有许多VPS，你可以用来做压力测试，威力也不小，linux攻击效果比WINDOWS好不止一倍，所以说，用这个办法去攻击吧，别搞我就行~~~各路大神求放过~~~

下面我就为大家带来安装教程和使用方法

安装方法

yum install gcc

wget https://github.com/jlw345/siege/raw/master/siege-4.0.4.tar.gz

tar -zxf siege-4.0.4.tar.gz

cd siege-4.0.4

./configure;make

make install

以上就是一键安装命令一键就可以安装完毕，我们就已经更新到官网最新版本~

使用方法
siege -c 200 -r 20 http://baidu.com
#-c 200 并发200个用户 -r 20 重复循环20
1
2
siege -c 200 -r 20 http://baidu.com
#-c 200 并发200个用户 -r 20 重复循环20
以上是基本命令，假如说你还想使你的攻击力加强请请看下面的参数详解

参数详解
-C,或–config 在屏幕上打印显示出当前的配置,配置是包括在他的配置文件$HOME/.siegerc中,可以编辑里面的参数,这样每次siege 都会按照它运行.

-v 运行时能看到详细的运行信息

-c n,或–concurrent=n 模拟有n个用户在同时访问,n不要设得太大,因为越大,siege 消耗本地机器的资源越多

-i,–internet 随机访问urls.txt中的url列表项,以此模拟真实的访问情况(随机性),当urls.txt存在是有效

-d n,–delay=n hit每个url之间的延迟,在0-n之间

-r n,–reps=n 重复运行测试n次,不能与 -t同时存在

-t n,–time=n 持续运行siege ‘n’秒(如10S),分钟(10M),小时(10H)

-l 运行结束,将统计数据保存到日志文件中siege .log,一般位于/usr/local/var/siege .log中,也可在.siegerc中自定义

-R SIEGERC,–rc=SIEGERC 指定用特定的siege 配置文件来运行,默认的为$HOME/.siegerc

-f FILE, –file=FILE 指定用特定的urls文件运行siege ,默认为urls.txt,位于siege 安装目录下的etc/urls.txt

-u URL,–url=URL 测试指定的一个URL,对它进行”siege “,此选项会忽略有关urls文件的设定

url.txt文件：是很多行待测试URL的列表以换行符断开,格式为:

[protocol://]host.domain.com[:port][path/to/file]

用法举例：

siege -c 300 -r 100 -f url.txt

说明：-c是并发量，-r是重复次数。url.txt就是一个文本文件，每行都是一个url，它会从里面随机访问的。
