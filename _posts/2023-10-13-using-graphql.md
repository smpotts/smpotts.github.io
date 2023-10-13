---
layout: post
title: GraphQL as an alternative to REST APIs
subtitle: I tried GraphQL and I really liked it
cover-img: /assets/img/fairplay.jpg
thumbnail-img: /assets/img/fairplay.jpg
share-img: /assets/img/fairplay.jpg
tags: [tech, graphql, ruby, ruby_on_rails]
---

I was perusing the Ruby on Rails courses on Udemy recently and came across a [course](https://www.udemy.com/course/basics-of-graphql-with-ruby-on-rails/) on using GraphQL with Ruby on Rails. It was a short hour and a half of video content, so I purchased it and followed along with the videos. The course instructor, Alex Deva, does an awesome job explaining the concepts and walking through small projects that demonstrate how and when to use GraphQL. I had heard of GraphQL before, but I didn't have any exposure to it up until this course. 

GraphQL is an alternative to using a REST API where you have two pieces of software (like a backend and a frontend) that need to communicate with each other. In a lot of cases, the underlying data for the application needs to change based on things that happen, for instance when the user takes some sort of action like clicking a button. With GraphQL you create queries to describe the exact data you want to get back. The idea with GraphQL is that you get back exactly what you need instead of having to deal with additional data that isn't necessary, which you often do with REST.

The course recommends installing [GraphiQL](https://github.com/graphql/graphiql), and I really enjoyed working with it. GraphiQL was pretty easy to install and it's very simple and lightweight. You have to add ```gem "graphql"``` to your Gemfile and start the rails server, then you can start interacting with GraphiQL on port 3000.

[![Screenshot-2023-10-13-at-6-45-15-AM.png](https://i.postimg.cc/YqQGpc7D/Screenshot-2023-10-13-at-6-45-15-AM.png)](https://postimg.cc/SJNNrvJc)

With GraphQL you read data through the use of queries. By default the project creates a file called ```query_type.rb``` where you can define root level fields which can be added as a data point to retrieve in the queries. The example test field it provides looks like this:
```
    field :test_field, String, null: false,
      description: "An example field added by the generator" do
      argument :name, String, required: true
    end

    def test_field(name:)
      Rails.logger.info context[:time]
      "Hello #{name}!"
    end
```
Each field has a corresponding method which defines some actions that will be taken on the backend. For instance if you have a login query that has a username and password as parameters, the method will do something like look up and authenticate the user, create a session, etc.

Queries get a lot more interesting when you use them in combination with ActiveRecord objects. When you want to return data from an object in ActiveRecord, you can define a new type that defines fields and their corresponding methods from the class. An example would be something like this:
```
class Types::PersonType < Types::BaseObject
  description "Defines a person"

  field :id, ID, null: false
  field :first_name, String, null: true
  field :last_name, String, null: true
  field :full_name, String, null: true

  def full_name
    "#{object.first_name} #{object.last_name}"
  end
end
```

This was hard to wrap my head around at first because the root level fields in the ```query_type.rb``` file also extend ```Types::BaseObject```, but I guess the way I think of it is that those are more general/ project level fields, whereas fields defined in their own Type classes are specifically for that ActiveRecord object. I grew to appreciate the way this is organized so everything isn't jammed into one file.

Mutations are the other key component of GraphQL, and those are used to write/ update data. When the project is generated it creates a ```mutation_type.rb``` file, containing fields and methods for mutations similiar to how they are set up for queries. The methods for the fields in the ```mutation_type.rb``` class are going to do some type of creating or updating of the underlying data.

You can simplify the creation of a mutation by creating an InputType, which defines a data structure that can be used as an input for the mutation, instead of having to list out every attribute of the object it should return.

```
class Types::PersonInputType < GraphQL::Schema::InputObject
  graphql_name "PersonInputType"
  description "All the attributes needed to create/ update a person"

  argument :id, ID, required: false
  argument :first_name, String, required: false
  argument :last_name, String, required: false
  argument :full_name, String, required: false
end
```
So then when you go to create a mutation to create a new instance of Person in this case, you can simply write:
```
mutation createPerson($person:PersonInputType!){
  createPerson(person: $person) {
    id
    fullName
  }
}
```
Of course this is assuming you have a field and method called "create_person" that look something like this:
```
module Types
  class MutationType < Types::BaseObject
    field :create_person, Types::PersonType, mutation: Mutations::CreatePerson
end
```
And then:
```
class Mutations::CreatePerson < GraphQL::Schema::Mutation
  # nullability
  null true

  argument :person, Types::PersonInputType, required: true

  def resolve(person:)
    Person.create(person.to_h)
  end
end
```

Overall I thought the Udemy course was excellent, and I would love to spend more time working with GraphQL. It's a really fun and interesting way to interact with APIs.

Photo: Fairplay, CO