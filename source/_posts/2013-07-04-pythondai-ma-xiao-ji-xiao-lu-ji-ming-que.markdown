---
layout: post
title: "python代码小记-效率及明确"
date: 2013-07-04 19:46
comments: true
categories: [Python] 
footer: true
---

今天写了一段代码，结果改了好几次，特此记录一下。

功能：传入任意字符，将其decode为unicode字符。

{% codeblock version1 lang:python %}
import chardet
def convert_charset_to_unicode(charset, default='utf-8'):
    charset_encoding = chardet.detect(charset).get('encoding') or default
    return charset.decode(charset_encoding, 'ignore')
{% endcodeblock %}

问题：

*    效率低下，通常大多数需要decode字符都是utf-8，也就是说只有少数的情况下需要detect
     encoding。而现在的情况是每次decode都需要detect，而detect这个操作比较重，因此需要就效率进行一次优化。

{% codeblock version2 lang:python %}
import chardet
def convert_charset_to_unicode(charset, default='utf-8'):
    try:
        return charset.decode(default)
    except:
        charset_encoding = chardet.detect(charset).get('encoding') or default
        return charset.decode(charset_encoding, 'ignore')
{% endcodeblock %}


问题：

*    没有明确定义错误类型，当使用try..except..时，一般异常明确的时候需要指出其异常类型。

{% codeblock version3 lang:python %}
import chardet
def convert_charset_to_unicode(charset, default='utf-8'):
    try:
        return charset.decode(default)
    except UnicodeDecodeError:
        charset_encoding = chardet.detect(charset).get('encoding') or default
        return charset.decode(charset_encoding, 'ignore')
{% endcodeblock %}


小结：注重效率以及明确异常类型。
