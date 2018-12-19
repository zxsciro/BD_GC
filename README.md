#
#在调研过程中，经常需要对一些网站进行定向抓取。由于python包含各种强大的库，使用python做定向抓取比较简单。请使用python开发一个迷你定向抓取器mini_spider.py，实现对种子链接的广度优先抓取，并把URL长相符合特定pattern的网页保存到磁盘上。

可以使用Python3，鼓励使代码支持setuptools。

程序运行:
    python mini_spider.py -c spider.conf

配置文件spider.conf:
    [spider] 
    url_list_file: ./urls ; 种子文件路径 
    output_directory: ./output ; 抓取结果存储目录 
    max_depth: 1 ; 最大抓取深度(种子为0级) 
    crawl_interval: 1 ; 抓取间隔. 单位: 秒 
    crawl_timeout: 1 ; 抓取超时. 单位: 秒 
    target_url: .*.(gif|png|jpg|bmp)$ ; 需要存储的目标网页URL pattern(正则表达式) 
    thread_count: 8 ; 抓取线程数

种子文件每行一条链接，例如:
    http://www.baidu.com/
    http://www.sina.com.cn/

要求和注意事项:
    1. 需要支持命令行参数处理。具体包含: -h(帮助)、-v(版本)、-c(配置文件)
    2. 需要按照广度优先的顺序抓取网页。
    3. 单个网页抓取或解析失败，不能导致整个程序退出。需要在日志中记录下错误原因并继续。
    4. 当程序完成所有抓取任务后，必须优雅退出。
    5. 从HTML提取链接时需要处理相对路径和绝对路径。
    6. 需要能够处理不同字符编码的网页(例如utf-8或gbk)。
    7. 网页存储时每个网页单独存为一个文件，以URL为文件名。注意对URL中的特殊字符，需要做转义。
    8. 要求支持多线程并行抓取。
    9. 代码严格遵守百度python编码规范
    10. 代码的可读性和可维护性好。注意模块、类、函数的设计和划分
    11. 完成相应的单元测试和使用demo。你的demo必须可运行，单元测试有效而且通过
    12. 注意控制抓取间隔和总量，避免对方网站封禁百度IP。

提示(下面的python工具或库可能对你完成测试题有帮助):
    virtualenv/pipenv(构造开发环境)
    re(正则表达式)
    gevent/threading(多线程)
    docopt/getopt/argparse(命令行参数处理)
    ConfigParser(配置文件读取)
    urllib/urllib2/httplib(网页下载)
    pyquery/beautifulsoup4/HTMLParser/SGMLParser(HTML解析)
    urlparse(URL解析处理)
    logging(日志处理)
