[![General Assembly Logo](https://camo.githubusercontent.com/1a91b05b8f4d44b5bbfb83abac2b0996d8e26c92/687474703a2f2f692e696d6775722e636f6d2f6b6538555354712e706e67)](https://generalassemb.ly/education/web-development-immersive)

# Intro Section
Not sure what will go here yet.


## Prerequisites
* GraphQL and GraphiQL
* Understanding of how to read and write GraphQL Queries

## Objectives

By the end of this, developers should be able to:
* Setup Apollo Client within a React Application
* Fetch Data from a GraphQL API
* Render Fetched Data from a GraphQL API via React Components

## Installing Apollo Client
1. Clone down this React [starter app](#)
2. cd into the project and run `npm i`
3. Run `npm install apollo-boost @apollo/react-hooks graphql`
   * `apollo-boost`: Package containing everything you need to set up Apollo Client
   * `@apollo/react-hooks`: React hooks based view layer integration
   * `graphql`: Also parses your GraphQL queries
4. Open the app in VS Code


Better preparation instructions may be found as
[snippets](https://github.com/ga-wdi-boston/instructors/tree/master/snippets).

### What is Apollo
Give a brief overview of Apollo and how it allows you to handle fetching and rendering GraphQL within a React application.

This section will be a high level overview.



### Performing API Calls With Apollo Client
* `I Do`, `We Do` section where we walk students through performing API calls to GraphQL endpoint.
* Plan to use a free public GraphQL API.

We will continue to use the [Countries GraphQL API](https://countries.trevorblades.com/) in this lesson.

Open the `App.js` file and clear out the starter code with the following:
```jsx
import React from 'react';
import ApolloClient, { gql } from "apollo-boost";
import { ApolloProvider } from '@apollo/react-hooks';
import { useQuery } from '@apollo/react-hooks';

const client = new ApolloClient({
  uri: `https://countries.trevorblades.com/`
})

const App = () => (
  <ApolloProvider client={client}>
    <div>
      <h2>My first Apollo app 🚀</h2>
    </div>
  </ApolloProvider>
);

```

**Talk through what this code snippet does.**

Next we will add the query to our code. After the `client` variable and before the `App` component add the `query` variable:
```jsx
const getUsers = gql`
    query {
        countries {
            name
            emoji
        }
    }
`
```

**Talk through what this code snippet does.**


Now we will create a function that handles our API call to the GraphQL, we will start by just `console logging` the data that is returned from our query:

```jsx
function Countries() {
  const { loading, err, data } = useQuery(getUsers)

  if (loading) return <p>Loading....</p>
  if (err) return <p>Error....</p>

  console.log(data)
  return <p>I worked</p>
}

const App = () => (
  <ApolloProvider client={client}>
    <div>
      <h2>My first Apollo app 🚀</h2>
      <Countries />
    </div>
  </ApolloProvider>
);

export default App;

```

Explain that we now have to render the `Countries` component in order to see the returned data in the console.

**Talk through what this code snippet does.**

```jsx
function Countries() {
  const { loading, err, data } = useQuery(getUsers)

  if (loading) return <p>Loading....</p>
  if (err) return <p>Error....</p>

  return data.countries.map((country, i) => (
    <div key={i}>
      <p>{country.name}: {country.emoji}</p>
    </div>
  ))
}
```
Finally we will are able to render our returned data in the `App` Component:

**Talk through what this code snippet does.**



### Rendering Fetched GraphQL Data in React
* `I Do`, `We Do` section where show students how to render fetched GraphQL data via React Components.


## Interacting with GraphQL Data in React
This section of the lesson will introduce students to:
1. Performing API Calls With Apollo Client
2. Rendering Fetched GraphQL Data in React
3. GraphQL Variables


## GraphQL Variables
Will explain GraphQL variables and how they provide a better way to set up dynamic values in operations

* This section will have a `I Do` and `We Do`

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

- Any useful links should be included in the talk material where the link is first referenced.
- Additional links for further study or exploration are appropriate in this section.
- Links to important parts of documentation not covered during the talk, or tools tangentially used but not part of the focus of the talk, are also appropriate.

## [License](LICENSE)

**?Is this the correct information for this section?**
1. All content is licensed under a CC­BY­NC­SA 4.0 license.
2. All software code is licensed under GNU GPLv3. For commercial use or alternative licensing, please contact legal@ga.co.
