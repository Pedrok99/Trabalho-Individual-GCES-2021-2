FROM ruby:3.0.0

WORKDIR /gces

COPY . .

RUN gem install rails bundler

RUN bundle install

#Download and install node + yarn
RUN curl https://deb.nodesource.com/setup_12.x | bash

RUN curl https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -

RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

RUN apt-get update -qq && apt-get install -y nodejs yarn

# Expose port 3000
EXPOSE 3000

# Build assets, set up database, and run server
CMD rails assets:precompile && rails db:setup && rails server -p 3000 -b 0.0.0.0