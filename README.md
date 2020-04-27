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
      resources :facts
    end
  end
end
```
- update both UsersController and FactsController
- Enter console by `rails c`
```
$ oliver = User.create( username: 'Oliver', password: 'password' )

$fact_one = Fact.create( fact: 'Wiley Hardeman Post was the first pilot to fly solo around the world.', likes: 1, user_id: 1 )

$ fact_two = Fact.create( fact: 'The Symphony No1 in E flat major, K.16, was written by Wolfgang Amadeus Mozart at the age of 8.’ likes: 2, user_id: 1 )

$ exit
```
- `rails server | s`
- http://localhost:3000/api/v1/users
- http://localhost:3000/api/v1/users/1/facts
- http://localhost:3000/api/v1/facts


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