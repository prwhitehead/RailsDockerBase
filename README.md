# Rails Docker Base

This is a template for creating Docker based Rails development environments.

## Get Started

```bash
docker-compose run --no-deps rails rails new . --skip-coffee --webpack=stimulus --database=mysql
```

Update the `config/database.yml` with the correct database credientials and create the database:

```yml
adapter: mysql2
encoding: utf8mb4
pool: <%= ENV.fetch("RAILS_MAX_THREADS") { 5 } %>
username: root
password: root
host: db
```

Add the Gems you want, ie:

```Gemfile
gem "anycable-rails", "~> 1.0"
gem "connection_pool"
gem "hiredis"
gem 'redis', '~> 4.0', require: ["redis", "redis/connection/hiredis"]
gem "sidekiq"
gem "stimulus_reflex"

group :development, :test do
  gem 'pry-byebug'
end
```

To install, `docker-compose exec rails bundle install`
