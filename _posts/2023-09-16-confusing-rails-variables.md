---
layout: post
title: Bewildering language features in Ruby
subtitle: A few things I found puzzling, yet very powerful
cover-img: /assets/img/int_tennis_hof.jpg
thumbnail-img: /assets/img/int_tennis_hof.jpg
share-img: /assets/img/int_tennis_hof.jpg
tags: [ruby, ruby_on_rails, syntax]
---

I didn't have any experience with Ruby on Rails prior to joining eSpark Learning, and I've been learning it on the go by jumping into our Rails projects to make contributions. Though I have worked with a few other object oriented programming languages in the past, Ruby on Rails feels very different from the rest. I think part of this is due to the fact that Ruby on Rails follows an MVC (model-view-controller) model, but I also find the syntax of the language very challenging. I wanted to break down some of the most confusing syntactical forms I've seen and struggled with.

## Symbols
One of the most confusing things I have come across in Ruby are symbols. Symbols look like `:name` and they appear to be variables at first glance, but they are actually their own construct. They essentially represent an object that is immutable, and can be passed in as arguments to methods. I found this [Medium article](https://medium.com/rubycademy/symbol-in-ruby-daca5abd4ab2) particularly helpful in breaking down what a symbol is in Rails. The article mentions that a symbol can be a method, a variable, a hash key, a state, etc.

One example where I've seen symbols is in migration statements:
```
class CreateUsers < ActiveRecord::Migration[7.0]
  def change
    create_table :users do |t|
      t.string :username
      t.string :password
      t.timestamps
    end
  end
end
```

In this example, the column names on the table are symbols.

## Keys
Keys look very similar to symbols, and they look like `key:` in the code. This notation is shorthand for accessing an element of a [Hash](https://ruby-doc.org/core-2.2.0/Hash.html). The Ruby docs describe a Hash as "a dictionary-like collection of unique keys and their values". This is similar to the `dict` data structure in Python. The places where I often see keys used is in object create statements or in method declarations as parameters, for example:
```
def test(param_name:)
    # do something
end
```

It's not super intuitive at first, but hashes can be used as parameters to a method. I really like the way Justin Weiss demonstrates the use of hashes as parameters in this article, ["Fun With Keyword Arguments, Hashes, and Splats"](https://www.justinweiss.com/articles/fun-with-keyword-arguments/).

## Safe Navigation Operators
The safe navigation operators are a super useful language feature in Ruby which allows you to avoid `NilClass` exceptions. They typically come up in a scenario like this:
```
user = User.where(email: email).first&.authenticate(password)
```

Without the addition of the `&` in this statement, if the user we are looking for didn't exist, this line would throw a `NilClass` exception. This is because `User.where(email: email).first` would be `nil` and then we are trying to call `.authenticate(password)` on a `nil` object. The addition of the `&` operator means it will only call the resulting part of the statement if the object thus far is not `nil`. So in this scenario, if the user did not exist, the whole statement would just return `nil` instead of erroring out.

## Triple Equals Operators
The triple equals operator is a powerful expression in Ruby that is used quite often. Despite the way it looks (similar to `==`), it has nothing to do with equality. Brandon Weaver wrote an awesome explanation breaking down all the different uses of `===` in this article,  ["Understanding Ruby Triple Equals"](https://dev.to/baweaver/understanding-ruby-triple-equals-2p9c). Essentially the `===` operator has lots of different uses like checking to see if something is included in a set, checking to see whether something matches a regular expression, checking data types, and more. Most recently, I used it in a scenario where I needed a regular expression to see if a subset of a String was a part of a larger String like this:
```
/sub/ === 'substring'
```

There are many more confusing and powerful language features I've learned in Ruby, and many more I have yet to encounter, but these are a few I find especially valuable to understand.

Photo: International Tennis Hall of Fame in Newport, RI