---
layout: post
category : markdown
tags : [markdown]
---
{% include JB/setup %}

syntax testbed 

## 语法 ``` 被github 支持，可是我的jekkel不支持，so...

```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

## jykkel 支持的样子

{% highlight java %}
public class HelloWorld {

    public static void main(String[] args) {
        System.out.println("Hello, World");
    }

}
{% endhighlight %}


## [or by highlighter.js]（http://stackoverflow.com/questions/8648390/syntax-highlighting-markdown-code-blocks-in-jekyll-without-using-liquid-tags）

Here is some Ruby code.

<pre>
  <code class="ruby">
    puts "hello"
  </code>
</pre>