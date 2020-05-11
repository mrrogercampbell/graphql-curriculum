[![General Assembly Logo](https://camo.githubusercontent.com/1a91b05b8f4d44b5bbfb83abac2b0996d8e26c92/687474703a2f2f692e696d6775722e636f6d2f6b6538555354712e706e67)](https://generalassemb.ly/education/web-development-immersive)

# What is GraphQL?

GraphQL is a new API standard that was developed and open-sourced by Facebook with the intent to be a more efficient, powerful and flexible alternative to REST.

Some consider GraphQL a database technology but this is incorrect, it is a **query language** for APIs.

GraphQL utilizes **declarative data fetching**, this allows a client to specify the exact data it wants from an API. Instead of utilizing multiple endpoints that all return static data structures, a GraphQL server only exposes a single endpoint and responds with the exact data the client is requesting.

## Prerequisites
* Basic Understanding of JavaScript:
  * Syntax
  * Data Types
  * Functions and Methods

## Objectives

By the end of this, developers should be able to:

* Explain the difference between:
  * REST & GraphQL
  * GraphQL and GraphiQL
* Know how to utilize GraphQL Playground and GraphiQL
* Be able to read and write GraphQL basic and nested queries

## Preparation

1. Fork and clone this repository. [FAQ](https://github.com/ga-wdi-boston/meta/wiki/ForkAndClone)
1. Create a new branch, `training`, for your work.
1. Checkout to the `training` branch.
1. Install dependencies with `npm install`.

Better preparation instructions may be found as [snippets](https://github.com/ga-wdi-boston/instructors/tree/master/snippets).

It's a good idea to have students do these steps while you're writing objectives on the whiteboard.

## REST vs GraphQL
REST is the go to design pattern for most legacy backend applications, GraphQL is very quickly becoming the new norm. Each design pattern has it benefits and limitations.


### REST APIs
`REST` is an `API design architecture` for web services. RESTful web services are used to retrieve and manipulate data that is stored within a web service via HTTP methods, such as GET. POST,  PUT, and DELETE. The core principle of REST is that everything is a resource which is identifiable by a URL.

**Benefits of a REST APIs**
* Scalability
  * It  allows Engineers to modularize the client and server separately so that they are able to scale each indefinitely.
* Flexibility
  * Engineers are able to design and develop REST APIs to receive different variations of request based off of user requirements and return data accordingly.

**Limitations of a REST APIs**
* Over-fetching
  * When the client downloads more data then is needed for the application.
* Under-fetching
  * When an endpoint does not provide enough data for the so the application has to make multiple API request

### GraphQL APIs
The GraphQL API design architecture was created with a more flexible approach to requesting and responding with data. The main difference between GraphQL and REST is that GraphQL can get retrieve the data your application needs in a single request. GraphQL can do this because it regards all data in a web service as either types and fields, not endpoints. With this unique design pattern, you can access all your data from a single endpoint versus multiple.

**Benefits of GraphQL APIs**
* Self Generating Documentation
  * GraphQL has the ability to self document your API based on the code you write.
* No Need For Overfetching
  * Due to the flexibility of GraphQL's query language Engineer can request the specific data that want when they want.
* Strong Type System
  * The API's capabilities are defined clearly so that the client knows exactly how to access data.

**Limitations of a GraphQL APIs**
* Single Endpoint
  * Where this is one of the greatest benefits, it can also cause a lot of issues when dealing with HTTP specification for caching.
* Bloated Pattern For Small Applications
  * If you need a straight forward API for simple CRUD, than REST is probably your best approach due to the fact GraphQL can be a bit of heavy lifting for initial setup.

#### Interacting with a GraphQL API via GraphQL Playground - We Do
As mentioned before, GraphQL has the ability to `self generate documentation` based off the code you write. A question you might ask is how and where are you able to view said documentation? The answer is `GraphQL Playground`.

`GraphQL Playground` is a GraphQL `Integrated Development Environment (IDE)`. It is built on top of another `GraphQL IDE`called `GraphiGL`.

For now we will focus on utilizing `GraphQL Playground`, let navigate to the [Countries GraphQL API](https://countries.trevorblades.com/) and take a look at `GraphQL Playground` in action.

Here you will see the GraphQL Playground IDE interface. We will learn how to interact with this shortly.
![Countries GraphQL API Playground Landing Page](https://git.generalassemb.ly/DC-WDI/GraphQL/blob/master/working-with-graphql-api/assets/graphql-playground-landing.png?raw=true)]

If you look to the right hand side of the site you will see two buttons `DOCS` and `SCHEMA`.


##### GraphQL Playground DOCS
Let's start by clicking the `DOCS` button.

This here is part of GraphQL's `self generate documentation`. GraphQL Playground does add some extra feature to this. What we see below is documentation on all the queries that this GraphQL endpoint can handle.
![Countries GraphQL API Playground Docs Image 1](https://git.generalassemb.ly/DC-WDI/GraphQL/blob/master/working-with-graphql-api/assets/graphql-playground-docs-1.png?raw=true)

This documentation is also interactive, meaning you are able to click on a query to see what `fields` you are able to pass in.

Try clicking the `countries` query.
![Countries GraphQL API Playground Docs Image 2](https://git.generalassemb.ly/DC-WDI/GraphQL/blob/master/working-with-graphql-api/assets/graphql-playground-docs-2.png?raw=true)

Now you are able to see all the fields that you are able to query and their corresponding types. We will review the GraphQL `Type System` in the next section of this lesson.

##### GraphQL Playground Schema
Next we will take a look at the Schema documentation that is generated within GraphQL Playground.

Click on the `Schema` button, this tab describes all the functionality offered by this GraphQL endpoint.

![Countries GraphQL API Playground Schema](https://git.generalassemb.ly/DC-WDI/GraphQL/blob/master/working-with-graphql-api/assets/graphql-playground-schema.png?raw=true)


The topic of a Schema within the bounds of GraphQL could be broken into a completely separate lesson. For now all you need to know is that this tab will show you what:
* Fields are within each data model of the backend
* Type of queries can be performed on each model and how to perform them

We will get a clear understanding of GraphQL Schemas once we start design and developing our own GraphQL APIs.


#### GraphQL Type System

Each `field` has a `type`. The `type` defines what kind of data will be returned for that field.

GraphQL has a `Type System` which defines the various data types that can be used by a GraphQL application.

There are 5 Types in GraphQL:
1. Scalar
   * These are primitive data types that can only store a single value
     * Int, Flat, String, Boolean, ID
2. Object
   * Most common type and is used in a schema to represent a group of fields.
3. Query
   * Used to get data from the server. How you instantiate `READ` functionality on a GraphQL server.
4. Mutations
   * Denotes the requests that instantiate `Create`, `Update`, and `Delete` functionality on a GraphQL server.
5. Enum
   * Similar to a `scalar type`, this type is used when the value for a filed must be from a set list of options.



#### GraphQL Queries

There are three operations that can be performed in a GraphQL API:
1. Query
    * Used to `fetch` data
2. Mutation
   * Lets `change` data
3. Subscription
   * Allows you to `watch` data for changes

For now we will just focus on how to work with a `query`.

Queries allow the client to fetch exactly what data it would like to receive from the server.

Before we interact with a GraphQL server we must define what operations we want to perform.

```graphql
query{

}
```
The syntax above is the basic building blocks to requesting data from a GraphQL server. As it stand right now we are not requesting any data. All we are doing is defining the operation that perform, which is a `query`.

In order to request information within our `query` we must specify what data `type` and  `field(s)` we want to receive data for.

In the `query` below we are:
1. Accessing the `countries` data type which is an `object` type.
2. Querying data for the `name` field.
```graphql
query{
  countries{
    name
  }
}
```
Try performing this query in the GraphQL Playground.
<details>
  <summary>What data does this return?</summary>
<p>It returns all the countries that are stored inside of the database.</p>

```graphql
  {
  "data": {
    "countries": [
      {
        "name": "Andorra"
      },
      {
        "name": "United Arab Emirates"
      },
      {
        "name": "Afghanistan"
      },
      {
        "name": "Antigua and Barbuda"
      },
      {
        "name": "Anguilla"
      },
      {
        "name": "Albania"
      },
      {
        "name": "Armenia"
      },
      ...
    ]
  }
```

</details>


Not enough data? No problem, all you have to do is update you query for any other fields that you would like data for. Let's say you want to request the `name`, `native`, and `emoji` for each country.
```graphql
query{
  countries{
    name
    native
    emoji
  }
}
```
As you can see GraphQL is super flexible in the way you can query data. If you want something just ask for if not leave it out.

#### Nested Query
You might be asking yourself why are the queries in the last section any different that sending a request to an REST API? Some of GraphQL's true power is utilizing `Nested Queries`.

A `Nested Queries` is when you request two different data `Types` or `models` within one request.

Lets say we want to see every `language` that is spoken in each `Country`.

```graphQL
query{
  countries{
    name
    native
    emoji
    languages{
      name
    }
  }
}
```

Let's breakdown what we just did above.
1. Initial we are querying the `countries` field which is linked to the `Country` type.
2. We then state that we would like to receive data for the `Country` type fields `name`, `native`, `emoji`, and `languages`.
3. `languages` is a field who's `type` is an `Object` just like `countries`.
4. By placing the `languages` field inside our `countries` query we are able to nest a `object` type inside of another.


<details>
  <summary>Try this query in GraphQL Playground. What data does it return?</summary>
<p>It returns all the countries and all the languages that are spoken in each country.</p>

```graphql
{
    "data": {
        "countries": [
            {
                "name": "Andorra",
                "native": "Andorra",
                "emoji": "🇦🇩",
                "languages": [
                    {
                        "name": "Catalan"
                    }
                ]
            },
            {
                "name": "United Arab Emirates",
                "native": "دولة الإمارات العربية المتحدة",
                "emoji": "🇦🇪",
                "languages": [
                    {
                        "name": "Arabic"
                    }
                ]
            },
            ...
        ]
    }
}
```

</details>

#### You Do
Perform a nested query with any other `Type`.






## Lab: Write a Lab
Plan to use [Challenge Template](https://git.generalassemb.ly/wdi-dc-instructors/homework-template)
Ideas for first lab:
  1. Provide students a link to a free public GraphQL API and have them query for specific data based on provided prompts.
  2. Provide students a link to a free public GraphqL API and matching REST API and have them query both APIs for the same data based on provided prompts.
      * This will allow then to see the benefits of querying a GraphQL API vs a REST API.
  3. Open to suggestions.

## Homework: Write a Homework
Plan to use [Challenge Template](https://git.generalassemb.ly/wdi-dc-instructors/homework-template)

Ideas for first Homework:
1. Not sure if I should mimic lesson here? Would really love feedback on what Zakk might like to see here.

## Additional Resources

* [GraphQL Docs](https://graphql.org/learn/)
* [GraphQL: Core Features, Architecture, Pros and Cons](https://www.altexsoft.com/blog/engineering/graphql-core-features-architecture-pros-and-cons/)
* [GraphQL vs REST](https://medium.com/@back4apps/graphql-vs-rest-62a3d6c2021d)
* [GraphQL - Type System - TutorialsPoint](https://www.tutorialspoint.com/graphql/graphql_type_system.htm)
* [🎮 Prisma GraphQL IDE for better development workflows](https://github.com/prisma-labs/graphql-playground)
* [Introducing GraphQL Playground | Prisma](https://www.prisma.io/blog/introducing-graphql-playground-f1e0a018f05d)

## [License](LICENSE)

**?Is this the correct information for this section?**
1. All content is licensed under a CC­BY­NC­SA 4.0 license.
2. All software code is licensed under GNU GPLv3. For commercial use or
   alternative licensing, please contact legal@ga.co.
