# binsync.net
## Running locally
First, you need to have Ruby and Gem installed, which may look like this:
```
sudo apt-get install ruby ruby-full build-essential gem -y && gem install bundler
```

Next, while in this repo, run:
```
bundle install
bundle exec jekyll serve
``` 
If you get an error on `bundle install`, you may need to change your gem path with `bundle config set path ~/.gem`.

And the site should be up! 
