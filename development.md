To install RVM+Ruby+Jekyll:
`\curl -sSL https://get.rvm.io | bash`
`source /PATH/TO/RVM`
`xcode-select --install` (optional)
`sudo chown -R $(whoami) /usr/local` (optional)
`rvm install ruby-2.3.3`
`rvm use ruby-2.3.3`
`gem install jekyll`
`gem install bundle`
`bundle install`

To run the development server (script from Github):
`jekyll serve`

To run the development server in production mode (script from CDN):
`JEKYLL_ENV=production jekyll serve`

To deploy:
`git push live master`
