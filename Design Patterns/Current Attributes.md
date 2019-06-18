## What is Current Attributes?

Abstract super class that provides a thread-isolated attributes singleton, which resets automatically before and after each request. This allows you to keep all the per-request attributes easily available to the whole system.

## Example

Access a `current_user` object in model.

```ruby
# app/models/current.rb
class Current < ActiveSupport::CurrentAttributes
  attribute :user
end

# app/controllers/user_controller.rb
class UserController < ApplicationController
  def index
    Current.user = current_user
  end
end

# app/models/event.rb
class Event < ApplicationRecord
  def current_user
    Current.user
  end
end
```
