

preparation:
 wget.exe 64bit


S0: 

mkdir cache

S1: Run RubyInstaller

wget -Ocache\rubyinst.exe http://rubyforge.org/frs/download.php/75848/rubyinstaller-1.9.3-p125.exe 
cache\rubyinst.exe  /verysilent /dir="C:\rb\" /tasks="assocfiles,modpath"

S2: download devkit 

wget -Ocache\dk.exe https://github.com/downloads/oneclick/rubyinstaller/DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe --no-check-certificate

S3 : Install devkit 

1. Extract Files
 
$cache\dk.exe  -ocache\devkit -y 

2. Run Installation Scripts
$cd cache\devkit
$chcp 936 # 改为local code page
$ruby dk.rb  init # 生成 config.yml ，把发现的ruby列表到这里
$ruby dk.rb review # 看看这个列表
$ruby dk.rb install
[INFO] Updating convenience notice gem override for 'C:/rb'
[INFO] Installing 'C:/rb/lib/ruby/site_ruby/devkit.rb'

3. Test DevKit Installation

$gem install rdiscount # 验证devkit可以工作，就是可以编译native extensions,比如rdiscount 
$ruby -rubygems -e "require 'rdiscount'; puts RDiscount.new('**Hello RubyInstaller**').to_html" 


S4. Installing Jekyll

gem install jekyll 
git clone https://github.com/plusjade/jekyll-bootstrap.git
cd jekyll-bootstrap
jekyll serve -w # 监视变化，立刻生成_site\
start http://localhost:4000

S5. Write first post
rake post title="hello"
edit _post\2013/05/27/hellol/
修改_config.yml 的auto = false ，这样

S6. 发布

随便找一个http server ,如nginx ，吧_site\** copy到root目录内，即可发布

## trouble shooting :

1.   invalid byte sequence @  $ ruby dk.rb init
A: chcp 936

2. c:\DevKit>ruby dk.rb init
[INFO] found RubyInstaller v1.9.3 at C:/Ruby193
C:/Ruby193/lib/ruby/1.9.1/win32/registry.rb:173:in `tr': invalid byte sequence in UTF-8 (ArgumentError)

URL ref: https://groups.google.com/forum/#!msg/rubyinstaller/zCj6ttx_GdI/LPFdToNc4O0J

3. $ gem install jekyll
ERROR:  Error installing jekyll:
	invalid gem format for C:/Ruby193/lib/ruby/gems/1.9.1/cache/yajl-ruby-1.1.0-x86-mingw32.gem

单独执行 gem install yajl-ruby 

安静卸载rubyinstall ， "C:\rb\unins000.exe" /verysilent 

help ref：http://www.jrsoftware.org/ishelp/index.php?topic=setupcmdline

4. $ gem install jekyll

如果使用powercmd，会导致build native extensions的时候挂起。必须要cmd.exe !
