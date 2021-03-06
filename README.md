# InstallRailsForRuby1.8.7
How to install Ruby on Rails for Ruby version 1.8.7

#### Aug 21 2017  

Following steps below may solve your problem...  

````
$ gem install i18n -v 0.6.11
$ gem install rake -v 10.5.0
$ gem install rack -v 1.6.4
$ gem install rack-cache -v 1.2

$ gem install rails -v 3.2.22.5
````

After successfully installed Rails on to Ruby version 1.8.7 environment, I've once failed to create new rails project because of SSL feature had not been included in Ruby 1.8.7 itself, so I followed the instruction described here(https://github.com/rbenv/ruby-build/issues/197), then solved the problem.

If you use 'coffee-rails' in your project, the dependent gem 'execjs' have to be the version '1.4.1' because newer version does not comfort to older Ruby's hash syntax.  
Your Gemfile should have following lines(if you use coffee-rails)

````
gem 'execjs', '1.4.1'
gem 'coffee-rails', '3.2.2'
````
(The version of coffee-rails may vary depend on your demand)

Currently known gems should have lower version number:

nokogiri: 1.5.11  
rubyzip: 0.9.9

Sample Gemfile:

````
source 'https://rubygems.org'
#

gem 'i18n', '0.6.11'
gem 'rake', '10.5.0'
gem 'rack-cache', '1.2'
gem 'execjs', '1.4.1'

gem 'rails', '3.2.22.5'

gem 'rubyzip', '0.9.9'
gem 'nokogiri', '1.5.11'

# Bundle edge Rails instead:
# gem 'rails', :git => 'git://github.com/rails/rails.git'

group :development, :test do
  gem 'sqlite3', '1.3.5'
  gem 'rspec-rails', '2.11.0'
end

group :asserts do
  gem 'sass-rails', '3.2.5'
  gem 'coffee-rails', '3.2.2'
  gem 'uglifier', '1.2.3'
end

gem 'jquery-rails', '2.0.2'

group :test do
  gem 'capybara', '1.1.2'
end

group :production do
  gem 'pg', '0.12.2'
end

````

I strongly recommend to remove Gemfile.lock file once after editing Gemfile, because some version dependency inflict unresolveable dependency loop if your old Gemfile.lock stil remain alive.  
(If you hear somebody says 'No need to remove Gemfile.lock', DO NOT BELIEVE IT!)  

-----

二つ個人的が疑問があって、一つは、  
「何故Rubyの世界ではこんなにバージョンによって違いがあって、みんな混乱しているのだろうか」  
と言うこと、そしてもう一つは、  
「Ｒｕｂｙってこんな感じなのにどうして古いバージョンを未だに使っている人が多いんだろう」  
ということ。  

開発者が「使うな」と言っているのだから、早く新しいバージョンに移行して欲しいっす。  

ビギナーからの切実なお願い。
