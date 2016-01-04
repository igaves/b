---
layout: post
title:  抓取采集,用CSS3选择器应该是趋势吧
date:   2016-01-04 12:59:59
categories: IT
---

正则类型的采集方式,已经略微复杂了,成本太高

最好的应该是在server端把页面执行掉,然后再分析DOM

{% highlight ruby %}
    require 'open-uri'
    require 'nokogiri'
    
    #最爽的,还是再此步骤,起一个server端的webkit,先把页面执行掉.
    #然后再进行抓去分析
    doc = Nokogiri::HTML(open("http://www.someserver.com/read/3951/"));
    
    links = []
    doc.css('#readerlist li a').each do |item|
      href = item.attribute('href')
      unless /javascript/ =~ href.to_s
        links.push "http://www.miaobige.com#{href.to_s}"
      else
        href.to_s.gsub(/(\d+)/){|m|
          links.push "http://www.miaobige.com/read/3951/#{m.to_i - 100}.html"
        }
      end
    end
    
    fd = IO.sysopen('output.txt','a+')
    
    f = IO.new(fd,'a+')
    
    links.each do |link|
      d = Nokogiri::HTML(open(link),nil,'GBK')
    
      puts "读取链接#{link.to_s}"
    
      title = d.css('title').inner_html.to_s.encode('utf-8','GBK',:invalid=>:replace,:undef=>:replace)
      f.puts title
      f.puts "\r\n"
    
      content = d.css('#content').inner_html.gsub(/<\/?\w+>/,'').to_s.encode('utf-8','GBK',:invalid=>:replace,:undef=>:replace,:replace => "?")
    
      f.puts content
      f.puts  "\r\n"
      f.puts "\r\n"
    end
    
    f.close
{% endhighlight %}

抓取过程
![抓取过程](/public/images/2016-01-04/finder-running.png)


抓取结果
![2015最后一张照片](/public/images/2016-01-04/finder-result.png)




