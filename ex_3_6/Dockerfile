FROM ruby:latest

COPY rails ./

EXPOSE 3000

RUN apt-get update && apt install -y --allow-unauthenticated nodejs && \
    nodejs -v && \
    gem install bundler && \
    bundle install && \
    rails db:migrate && \
	useradd -m app && \
	chown -R app /app

USER app

WORKDIR /app

CMD ["rails", "s"]