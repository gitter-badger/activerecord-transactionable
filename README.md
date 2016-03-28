# Activerecord::Transactionable

Provides a method, `transaction_wrapper` at the class and instance levels that can be used instead of `ActiveRecord#transaction`.

Useful as an example of correct behavior for wrapping transactions.

NOTE: Rails' transactions are per-database connection, not per-model, nor per-instance,
      see: http://api.rubyonrails.org/classes/ActiveRecord/Transactions/ClassMethods.html

## Installation

Add this line to your application's Gemfile:

```ruby
gem 'activerecord-transactionable'
```

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install activerecord-transactionable

## Usage

When creating, saving, deleting within the transaction make sure to use the bang methods (`!`) in order to ensure a rollback on failure.

```
car = Car.new(name: "Fiesta")
car.transaction_wrapper do
  car.save!
end
```

Also see the specs.

## Development

After checking out the repo, run `bin/setup` to install dependencies. Then, run `rake spec` to run the tests. You can also run `bin/console` for an interactive prompt that will allow you to experiment.

To install this gem onto your local machine, run `bundle exec rake install`. To release a new version, update the version number in `version.rb`, and then run `bundle exec rake release`, which will create a git tag for the version, push git commits and tags, and push the `.gem` file to [rubygems.org](https://rubygems.org).

## Contributing

Bug reports and pull requests are welcome on GitHub at https://github.com/pboling/activerecord-transactionable.

