# rails_guide

# Installation:
  1. rubyinstaller.org
  2. RUBY DEVELOPMENT KIT
  3. jruby.org
  4. jgem install rails -v 4.2.7.1
  5. jgem install bundler
  6. jgem install warbler

# Instructions:
  1. rails new <project name>
  2. add 'group :development' in Gemfile
  3. include 'gem 'warbler''
  4. create warble.rb in /config
    Warbler::Config.new do |config|
      config.webxml.rails.env = 'development'
      config.jar_name = 'myapp'
    end
  5. run 'bundler update'
  6. change production key in /config/secrets.yml
  7. Jruby does not support // Create a file called .jrubyrc in your user home folder. Add the following: cext.enabled=true
     warble war

# Notes:
  1. Ran into this problem as well. Solved it by setting a root route. In my case, root 'pages#home' in config/routes.rb
     If the root route is not set, you are redirected to localhost:3000
  2. JRuby uses therubyrhino instead of the therubyracer gem as a JavaScript engine
  3. Application currently uses the sqlite3 gem, which is not supported by JRuby. activerecord-jdbcsqlite3-adapter should be used instead.
  4. The SQLite database that our application uses is currently present in the application's directory. When the WAR file is generated, the database in its current state will be placed inside the WAR file. We do not want this, because any changes that are made to the database after deployment will     be overwritten if the application is redeployed.

Launch the war in any jvm server.
