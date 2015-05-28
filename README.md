# ActiveRecordBatteries

ActiveRecordBatteries is a simple library that aims to provide some basic, useful tools for your models without a lot of complexity.

## Modules

- *Paginable*, provides database pagination.
- *Sluggable*, provides slug support for your models, normally used for pretty urls.
- *Deletable*, provides logical deletes.
- *Filterable*, provides an easy way to filter your results.
- *RelationshipScopes*, provides a way to add scopes for your relationships in a single line.

## Getting started

ActiveRecordBatteries works with Rails 4+. You can add it to your Gemfile with:

```ruby
gem active_record_batteries'
```

Run the bundle command to install it.


## Usage

To load the batteries on your models:

```ruby
class Article < ActiveRecord::Base
  batteries! :sluggable, :paginable, :filterable, :relationship_scopes, :deletable
end
```

You can use any or all of them at the same time.

### Paginable

```ruby
class Article < ActiveRecord::Base
  batteries! :paginable

  page_items 10   # default is 25
end
```

```ruby
Article.pages                     # how many pages with the current page_items configuration.

Article.pages(15)                 # how many pages if we have 15 items per page

@articles = Article.paginate(2)   # Get page 2

@articles.current_page            # What page are we on?
=> 2

@articles.total_items             # How many items do we have in total?
=> 23

@articles.total_pages             # How many pages do we have?
=> 3

```

## Final remarks

We wrote this code as we built [Chopeo](https://www.chopeo.mx) because we found most solutions to these problems to be more complicated than they needed to be for our case.

Most people build things in a way that tries to work in every corner case. It is a great goal. For this library, our goal was to keep it as simple as possible. It should cover most situations.

If you have any questions or comments please feel free to contact me at ebobby@ebobby.org. Pull requests are welcome.

## Author

Francisco Soto <ebobby@ebobby.org>

Copyright © 2015 Francisco Soto (http://ebobby.org) released under the MIT license.
