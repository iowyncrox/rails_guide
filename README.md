# rails_guide

Installation:
  rubyinstaller.org
  RUBY DEVELOPMENT KIT
  jruby.org
  jgem install rails -v 4.2.7.1
  jgem install bundler
  jgem install warbler

Instructions
  rails new <project name>
  add 'group :development' in Gemfile
  include 'gem 'warbler''
  create warble.rb in /config
    Warbler::Config.new do |config|
      config.webxml.rails.env = 'development'
      config.jar_name = 'myapp'
    end
  run 'bundler update'
  change production key in /config/secrets.yml
  Jruby does not support // Create a file called .jrubyrc in your user home folder. Add the following: cext.enabled=true
  warble war

Notes:
  1. Ran into this problem as well. Solved it by setting a root route. In my case, root 'pages#home' in config/routes.rb
     If the root route is not set, you are redirected to localhost:3000
  2. JRuby uses therubyrhino instead of the therubyracer gem as a JavaScript engine
  3. Application currently uses the sqlite3 gem, which is not supported by JRuby. activerecord-jdbcsqlite3-adapter should be used instead.
  4. The SQLite database that our application uses is currently present in the application's directory. When the WAR file is generated, the database in its current state will be placed inside the WAR file. We do not want this, because any changes that are made to the database after deployment will     be overwritten if the application is redeployed.

Launch the war in any jvm server.