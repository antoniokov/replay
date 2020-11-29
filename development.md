To install RVM+Ruby+Jekyll:
`curl -sSL https://raw.githubusercontent.com/rvm/rvm/master/binscripts/rvm-installer | bash -s stable`
`source /PATH/TO/RVM`
`xcode-select --install` (optional)
`sudo chown -R $(whoami) /usr/local` (optional)
`rvm install ruby@latest`
`rvm use ruby-X.X.X`
`gem install jekyll`
`gem install bundle`
`bundle install`

To run the development server (script from Github):
`jekyll serve`

To run the development server in production mode (script from CDN):
`JEKYLL_ENV=production jekyll serve`

To deploy:
`git push live master`
