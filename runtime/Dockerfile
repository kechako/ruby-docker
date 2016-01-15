FROM ruby:latest
MAINTAINER Tomato Ketchup <r@554.jp>

WORKDIR /app
ONBUILD ADD Gemfile /app/Gemfile
ONBUILD ADD Gemfile.lock /app/Gemfile.lock
ONBUILD RUN ["/usr/local/bundle/bin/bundle", "install", "--without=development", "test", "--deployment"]
ONBUILD ADD . /app

EXPOSE 8080
CMD []
ENV APPSERVER webrick
ENV RACK_ENV production
ENTRYPOINT /usr/local/bundle/bin/bundle exec rackup -p 8080 /app/config.ru -s $APPSERVER -E $RACK_ENV
