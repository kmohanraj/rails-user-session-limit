## Logging in from another browser will kill any previous sessions


### 1.Installation 
Added to Gem to [Gemfile](Gemfile)
```
gem 'devise'
gem 'devise-security'
```

Run Bundle Install
```
bundle install
```


Then, install devise
```
rails g devise:install
```

Then, Create Model,
```
rails g devise model-name
```

Then, Create migration
```
rails g migration add_session_limitable_to_users unique_session_id
```

Then, Edit the migration file
```
class AddSessionLimitableToUsers < ActiveRecord::Migration[6.0]
  def change
    add_column :users, :unique_session_id, :string, limit: 20
  end
end
```

Then Create DB & Migrate
```
rails db:create db:migrate
```

### 2.Configuration
Then, Add to your code to user ```:session_limitable``` [user](user.rb)
```
class User < ApplicationRecord
  devise :database_authenticatable,
         :recoverable, :rememberable, :validatable, :password_archivable, :session_limitable

end

```

Then Start your rails application




