#Passenger

![Phusion Passenger](/images/phusion_banner.png){: .no-border}

**Reference website:** [http://www.modrails.com/documentation/Users%20guide.html](http://www.modrails.com/documentation/Users%20guide.html){: .reference}


[Phusion Passenger](http://www.modrails.com/) is an Apache module for deploying [Rack](http://rack.rubyforge.org/) applications. As Merb is built on Rack, you can easily run it on Passenger and [Ruby Enterprise Edition](http://www.rubyenterpriseedition.com/). Ruby Enterprise Edition is a version of Ruby 1.8.6 with improvements to Ruby's garbage collection, which can typically reduce an applications memory footprint by 33%. The following instructions are for Linux.

##Installing Ruby Enterprise Edition (REE)
Ruby Enterprise Edition can be installed along side a version of Ruby you currently have installed, as it will be installed into the <tt>/opt</tt> directory.

*Note:* You will need to have the development readline libraries installed if you want run Merb interactively.
### Download REE

    $ wget http://rubyforge.org/frs/download.php/41040/ruby-enterprise-1.8.6-20080810.tar.gz

### Install

    $ tar xzvf ruby-enterprise-1.8.6-20080810.tar.gz
    $ cd ruby-enterprise-1.8.6-20080810
    $ ./insaller


##Installing Passenger

    $ gem install passenger
    $ passenger-install-apache2-module

##Configuration

###config.ru
The following file needs to be placed into your Merb applications root directory:

    # config.ru
    require 'rubygems'

    # Uncomment if your app uses bundled gems.
    # gems_dir = File.expand_path(File.join(File.dirname(__FILE__), 'gems'))
    # Gem.clear_paths
    # $BUNDLE = true
    # Gem.path.unshift(gems_dir)

    require 'merb-core'

    Merb::Config.setup(:merb_root   => File.expand_path(File.dirname(__FILE__)),
                       :environment => ENV['RACK_ENV'])
    Merb.environment = "production" #Merb::Config[:environment]
    Merb.root = Merb::Config[:merb_root]
    Merb::BootLoader.run

    # Uncomment if your app is mounted at a suburi.
    # if prefix = ::Merb::Config[:path_prefix]
    #   use Merb::Rack::PathPrefix, prefix
    # end

    run Merb::Rack::Application.new


## Capistrano Task
