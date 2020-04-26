# Commands
- `rails new <project_name> --api --database=mysql` (optional -T for Rspec)
- `rails generate model User username:string password:string`
- `rails generate model Fact user:references fact:string likes:integer`
- Go to config/database.yml, update database config
- `rails db:setup`
- `rails db:migrate`
- `rails g controller api/v1/Users`
- `rails g controller api/v1/Facts`
- go to `config/routes.rb`, update routes into
```ruby
Rails.application.routes.draw do
  namespace :api do
    namespace :v1 do
      resources :users do
        resources :facts
      end
    end
  end
end
```

# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


#### Troubleshooting
- If libssl error is presented, try `brew reinstall openssl@1.1`
This suggestion also solved the issue with the same error
Mac OSX, with Catalina 10.15.3, running mysql 8.0.19, using Rails 5.2 (for what its worth) and already had openssl 1.1.1d installed with Homebrew.

gem uninstall mysql2
brew upgrade openssl
gem install mysql2 -- --with-opt-dir="$(brew --prefix openssl)"