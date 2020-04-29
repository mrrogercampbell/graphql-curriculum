### GraphQL Basics: Schemas and Queries
1. What is a Graph
2. GraphQL Queries
   * Three operations that can be performed in GraphQL
        1. Query: Fetches data
        2. Mutation: Changes data
        3. Subscription: Allows you to watch data for changes
   * `Query syntax` allows the client to describe exactly what data it would like back.
   * We define a query with the `operation name` followed by a selection set:

This query is not requesting any data and would be considered invalid.
```GraphQL
query {

}
```

This query is requesting a single field **course**
```GraphQL
query {
    course
}
```

The result of the above query would be structured like this
```JSON
{
    "data": {
        "course": "GraphQL"
    }
}
```
All response dat is return within the `data` property. We requested a single field of `course` and got back a `course` property which contains the `data` object.

* GraphQL Schema
  * GraphQL is self-documenting! Meaning that a GraphQL API exposes a schema that describes exactly what operation can be performed on the API and what data can be requested. Gone are the days of manual documentation, this play well with tools such as GraphQL Playground where you are able to validate the structure of your operations before ever attempting to send them to the server.


1. Nested GraphQL Queries
2. Setting up Babel
3. Creating Your Own GraphL API
4. GraphQL Scalar Types
5. Live Reload for GraphQL Yoga
6. Creating Custom Types
7.  Operation Arguments
8.  Working with Arrays: Part 1
9.  Working with Arrays: Part 2
10. Relational Data: Basics
11. Relational Data: Arrays
12. Challenge: Part 1 - 3
    * Potential Idea for labs

### GraphQL Basic Mutations
1. Creating Data with Mutations: Pt. 1
3. Defining a Mutation
4. Creating Data with Mutations: Pt. 2
5. The Input Type
6. Deleting Data with Mutations: Pt. 1
7. Deleting Data with Mutations: Pt. 2
8. A Pro GraphQL Project Structure: Pt. 1
9. A Pro GraphQL Project Structure: Pt. 2
10. Updating Data with Mutations: Pt. 1
11. Updating Data with Mutations: Pt. 2

### GraphQL Basic: Subscriptions
1. GraphQL Subscription Basics
2. Subscribing on the Client
3. Setting up a Comment Subscription
4. Setting up a Post Subscription
5. Expanding the Post Subscription for Edits and Deletions
6. Expanding the Comments Subscription for Edits and Deletions
7. Enums

### Database Storage with Prisma
1. Section Intro
2. Prisma Mac Setup
3. Prisma 101
4. Exploring the Prisma GraphQL API
5. Add Post Type to Prisma
6. Integrating Prisma into a Node.ks Project
7. Using Prisma Bindings
8. Mutations with Prisma Bindings
9. Using Async/Await with Prisma Bindings
10. Checking If Data Exists Using Prisma Bindings
11. Customizing Type Relationships
12. Modeling a Review System with Prisma: Set Up
13. Modeling a Review System with Prisma: Solution

### Authentication with GraphQL
1. Adding Prisma into GraphQL Queries
2. Adding Prima to Context
3. Integrating Operation Arguments
4. Refactoring Custom Type Resolvers
5. Adding Prisma into GraphQL Mutations
6. Adding Prisma into GraphQL Update Mutations: Pt. 1
7. Adding Prisma into GraphQL Update Mutations: Pt. 2
8. Adding Prisma into GraphQL Subscriptions
9. Closing Prisma to Outside World
10. Allowing for Generated Schemas
11. Storing Passwords
12. Property Storing Passwords
13. Creating Auth Tokens with JSON Web Tokens
14. Logging in Existing Users
15. Validating Auth Tokens
16. Locking Down Mutations (Users)
17. Locking Down Mutations (Post and Comments)
18. Locking Down Queries: Pt. 1
19. Locking Down Queries: Pt. 2
20. Locking Down Individual Type Fields
21. Fragments
22. Cleaning up Some Edge Cases
23. Locking Down Subscriptions
24. Token Expiration
25. Password Updates

### Pagination and Sorting with GraphQL
1. Section Intro
2. Pagination
3. Pagination Using Cursors
4. Working with createdAt and updatedAt
5. Sorting Data

### Authentication with GraphQL
1. Section Into: Production Deployment
2. Creating a Prisma Service
3. Prisma Configuration and Deployment
4. Exploring the Production Prisma Instance
5. Node.js Production App Development: Pt 1
6. Node.js Production App Development: Pt 2
7. Node.js Production Environment Variables

### Apollo Client and Testing GraphQL
1. Section Intro
2. Setting up a Test Environment
3. Installing and Exploring Jest
4. Testing and Assertions
5. Apollo Client in the Browser: Pt. 1
6. Apollo Client in the Browser: Pt. 2
7. Configuring Jest to Start the GraphQL Server
8. Testing Mutations
9. Seeding The Database with Test Data
10. Testing Queries
11. Expecting GraphQL Operations to Fail
12. Supporting Multiple Test Suites and Authentication
13. Testing with Authentication: Pt. 1
14. Testing with Authentication: Pt. 2
15. GraphQL Variables: Pt. 1
16. GraphQL Variables
17. GraphQL Variables: Pt. 2
18. Testing Comments
19. Testing Subscriptions
20. Test Case Ideas

### Creating a Boilerplate Project
1. Setting up a Test Environment
2. Using the Boilerplate Project

