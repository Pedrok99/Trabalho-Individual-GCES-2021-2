FROM ruby:3.0.0

WORKDIR /gces

RUN apt-get update -qq && apt-get install -y 

COPY . .

RUN gem install rails bundler

RUN bundle install

EXPOSE 3000

CMD rails db:setup && rails server -p 3000 -b 0.0.0.0