preparation:
 wget.exe 64bit

S1: download and Install Ruby with the RubyInstaller

wget http://rubyforge.org/frs/download.php/75848/rubyinstaller-1.9.3-p125.exe 
rubyinstaller-1.9.3-p125.exe 
安装，并且勾选 ruby到path内

S2: download devkit 

wget -O dk.exe https://github.com/downloads/oneclick/rubyinstaller/DevKit-tdm-32-4.5.2-20111229-1559-sfx.exe --no-check-certificate

S3 : Install devkit 

1. Extract Files
 
dk.exe  -o<DEVKIT_INSTALL_DIR> -y 

2. Run Installation Scripts
$cd <DEVKIT_INSTALL_DIR> 
$ruby dk.rb  init #to  generate the config.yml file to be used later in this Step. 

Your installed Rubies will be listed there . edit the generated config.yml file to include installed Rubies not automagically discovered or remove Rubies you do not want to use 

the DevKit with.

$ruby dk.rb review # to review the list of Rubies to be enhanced to use the DevKit and verify the changes you made to it are correct. finally, 

$ ruby dk.rb install # to DevKit enhance your installed Rubies. 

This step installs (or updates) an operating_system.rb file into the relevant directory needed to implement a RubyGems pre_install hook and a devkit.rb helper library file into 

<RUBY_INSTALL_DIR>\lib\ruby\site_ruby. NOTE: you may need to use the --force option to update the above mentioned files as discussed at the SFX DevKit upgrade FAQ entry.

5. Test DevKit Installation

$gem install rdiscount -platform=ruby # Confirm your Ruby environment is correctly using the DevKit by running . RDiscount should install correctly and you should see 

Temporarily enhancing PATH to include DevKit… in the screen messages.

6. Next run 

$ ruby -rubygems -e "require 'rdiscount'; puts RDiscount.new('**Hello RubyInstaller**').to_html" 
# to confirm that the rdiscount gem is working.

7. Installing Jekyll
$gem install jekyll #Install Jekyll using  in your command prompt.

Clone Jekyll Bootstrap!
Go to the Jekyll Bootstrap website and follow the instructions there, then you’re done!

$ruby ./dk.rb install
[INFO] Updating convenience notice gem override for 'C:/Ruby193'
[INFO] Installing 'C:/Ruby193/lib/ruby/site_ruby/devkit.rb'

8. git clone https://github.com/plusjade/jekyll-bootstrap.git
9. Run
cd jekyll-bootstrap
jekyll serve
start http://localhost:4000

trouble shooting :

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


