source "https://rubygems.org"
# Hello! This is where you manage which Jekyll version is used to run.
# When you want to use a different version, change it below, save the
# file and run `bundle install`. Run Jekyll with `bundle exec`, like so:
#
#     bundle exec jekyll serve
#
# This will help ensure the proper Jekyll version is running.
# Happy Jekylling!
gem "jekyll", "~> 4.3.3"
gem "minimal-mistakes-jekyll", "4.24.0"

gem "rake"

# "rmagick" is a dependency of "jekyll-responsive-image"
gem "rmagick" # requires `apt-get install libmagickcore-dev`

# If you want to use GitHub Pages, remove the "gem "jekyll"" above and
# uncomment the line below. To upgrade, run `bundle update github-pages`.
# gem "github-pages", group: :jekyll_plugins
# If you have any plugins, put them here!
group :jekyll_plugins do
	gem "jekyll-archives"
	gem "jekyll-badges", :git => "https://github.com/santoso-wijaya/jekyll-badges.git"
	gem "jekyll-feed", "~> 0.12"
	gem "jekyll-include-cache"
	gem "jekyll-responsive-image"
end

# Lock `http_parser.rb` gem to `v0.6.x` on JRuby builds since newer versions of the gem
# do not have a Java counterpart.
gem "http_parser.rb", "~> 0.6.0", :platforms => [:jruby]
