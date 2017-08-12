# baike_spider
该项目用Python爬取百度百科1000个相关页面的URL、词条名称和简介。

乱码解决方法：

1.如果是URL部分乱码/item/%E7%BC%96%，是因为url采用了再编码-->16进制编码
解决方法：调用urllib.parse.unquote("/item/%E7%BC%96%")来变回中文
注意：变回中文的URL无法用urllib.request.urlopen(URL)来访问，可以在最后输出html的时候变回中文

2.输出的html分url,title,data三列，title和data出现\x96\x12\x34(unicode编码)
原因：因为先用encoding='utf-8'新建html文件，然后又fout.write("<td>%s</td>" % data['title'].encode('utf-8))又编码成unicode
解决方法：直接fout.write("<td>%s</td>" % data['title'])
