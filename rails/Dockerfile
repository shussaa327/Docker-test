FROM ruby:2.6

RUN curl -sL https://deb.nodesource.com/setup_10.x | bash - \ && apt-get install -y nodejs

ENV APP_HOME /app

WORKDIR $APP_HOME

COPY Gemfile $APP_HOME/Gemfile
COPY Gemfile.lock $APP_HOME/Gemfile.lock

RUN bundle install

RUN rails new . --database=mysql

COPY ./config $APP_HOME/config

VOLUME /app/public
VOLUME /app/tmp

CMD ["rails", "server", "-b", "0.0.0.0"]