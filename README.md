# Ruby wrapper for Quovo's v3 API (Not being developed/maintained)

## Requirements
### ruby 2.5.1
Developed on 2.5.1, will probably work on anything 2.3 and above.

### redis
Needed for caching the API's JWT.

## Installation

Add this line to your application's `Gemfile`:

```ruby
gem 'quovo-ruby'
```

Run:
```
bundle
```

Or install it yourself as:
```
gem install quovo-ruby
```
    
Go to wherever your initializers reside and create `quovo.rb`:
```ruby
require 'quovo-ruby'

Quovo.configure do |config|
  # Quovo API dashboard credentials
  config.username = ''
  config.password = ''
  
  # Outputs verbose HTTParty logging to stdout
  config.verbose = true
  
  # redis url for storing JWT
  config.redis_url = 'redis://localhost:6379'
end
````

## Usage
### Users
```ruby
Quovo.users.all
=> #<OpenStruct body=#<OpenStruct users=[{...}, {...}]>, headers={ ... }, status_code=200, success?=true>

Quovo.users.create(username: 'test_username', name: 'John Doe', email: 'test@example.com')
Quovo.users.find(1)
Quovo.users.destroy(1)
Quovo.users.update(1, email: 'new_email@example.com', name: 'John Smith')
```
### Accounts
```ruby
Quovo.accounts.all
Quovo.accounts.find(1)
Quovo.accounts
Quovo.accounts.for_user(2)
Quovo.accounts.for_connection(3)
Quovo.accounts.update(1, {???})
```