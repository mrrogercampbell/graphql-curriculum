[![General Assembly Logo](https://camo.githubusercontent.com/1a91b05b8f4d44b5bbfb83abac2b0996d8e26c92/687474703a2f2f692e696d6775722e636f6d2f6b6538555354712e706e67)](https://generalassemb.ly/education/web-development-immersive)

# GraphGL, React and Apollo
Not sure what will go here yet.


## Prerequisites
* GraphQL and GraphQL Playground
* Understanding of how to read and write GraphQL Queries

## Objectives

By the end of this, developers should be able to:
* Setup Apollo Client within a React Application
* Fetch Data from a GraphQL API
* Render Fetched Data from a GraphQL API via React Components


### What is Apollo
Give a brief overview of Apollo and how it allows you to handle fetching and rendering GraphQL within a React application.

This section will be a high level overview.


#### Installing Apollo Client
1. Cd into the [my-first-apollo-react-app](https://git.generalassemb.ly/DC-WDI/GraphQL/tree/master/graphql-react-and-apollo/my-first-apollo-react-app) located within the lesson repo
2. Run `npm i`
3. Run `npm install apollo-boost @apollo/react-hooks graphql`
   * `apollo-boost`: Package containing everything you need to set up Apollo Client
   * `@apollo/react-hooks`: React hooks based view layer integration
   * `graphql`: Also parses your GraphQL queries
4. Open the app in VS Code



#### Performing GraphQL Queries With Apollo Client - I Do
We will continue to use the [Countries GraphQL API](https://countries.trevorblades.com/) in this lesson.


#### Configuring the Client - We Do
Our first step is too create a `client instance`. This will allow us to tell the `Apollo Client` where we are expecting our data to come from.

Open the `App.js` file and clear out the starter code with the following:
```jsx
// App.js

import ApolloClient, { gql } from "apollo-boost";

const client = new ApolloClient({
  uri: `https://countries.trevorblades.com/`
})

```
Quick breakdown of what we did above:
1. Imported `ApolloClient` from `apollo-boost`
   * This allows us to utilize the `apollo-boost` depend within our react application.
2. Created a `client config object`
3. Added the `Countries API` endpoint to the `uri` property with in our `client config object`

#### Our First Query - We Do

Next we will create our initial `query`. We will utilize the `client instance` we create before and instantiate a `query method` on it.
```jsx
client.query()
```

The `query method` is allows us to define a GraphQL query and send it to the `uri` we defined within our `client config object`.

Now we are able to define our `query`. Copy the below code snippet under the `client config object`

```jsx
// App.js

client
  .query({
    query: gql`
    query {
        countries {
            name
            emoji
            currency
        }
    }
`
  })
  .then(res => console.log(res.data))

```
Quick breakdown of what we did above:
1. Instantiate a `query method` on the `client instance`
2. Pass a `object` as the argument to the `query method`
3. Define a GraphQL query by utilizing the `gql` function
   * This allows us to parse our string into a query document, like we use in GraphQL PLayground
   * **Be sure to alway use backticks when defining a `gql` function**
4. Rendering our data in the console.

Save your code and open the console, and just that easily you are able to request data from a GraphQL endpoint!


#### Your First Query - You Do
Now I want you to give this a shot. Complete the following:
1. Query the `countries` type for two more fields, one of those fields should be a nested field.
   * Be sure to check the `GraphQL Playground Docs` if you are unsure of what other fields are available.
2. Create a second separate query
   * Again, check the `GraphQL Playground Docs` if you are unsure what other queries are able to be handled



### Rendering Fetched GraphQL Data in React - We Do
Now that we know how to fetch data with a GraphQL query in vanilla `JavaScript`, it's time to learn how in React. The steps are very similar we just need to add a bit more logic.

#### Connecting the Client to React
We will start by updating our `App.js` file.
```jsx
// App.js
import { ApolloProvider } from '@apollo/react-hooks';

// ...

const App = () => (
  <ApolloProvider client={client}>
    <div>
      <h2>My first Apollo app 🚀</h2>
    </div>
  </ApolloProvider>
);
```
The Breakdown:
1. We import `ApolloProvider` from `@apollo/react-hooks`
   * This this is a `Wrapper Component` that we encase our React App in.
2. Wrap all the data and or components that are rendered in our application with a `ApolloProvider` Component.
3. We also added a `client` attribute to the `ApolloProvider` Component and gave it a value of the `client instance`.
   * This will allows us to access the `client` from anywhere within our component tree.

#### Defining a Query Variable - We Do
Now that we have successfully wired the `Apollo Client` to our React app. Its time to send our first request. Our next step is to replace our initial `query` within a variable.

On the line after our `client instance` deceleration and before the `App` component we need to create a variable to store our `query` within; for now lets call it `getUsers`:
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
The breakdown:
1. We define a variable called `getUsers`.
2. Then we declare a `gql` function and define a `GraphQL query` within it.

#### Requesting Data - We Do

Our next step is to utilize the `useQuery` hook to fire off a request to the `Countries API` so that we can eventually render said data, but for now we will just console log it.

Paste the code below into your `App.js` file.

```jsx
function Countries() {
  const { loading, error, data } = useQuery(getUsers)

  if (loading) return <p>Loading....</p>
  if (error) return <p>Error....</p>

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
The breakdown:
1. We create a `Countries` component.
   * This will handle our API call to the GraphQL server
2. Within our function we utilized the `useQuery` hook and passed our `getUsers` as an argument
   * The `useQuery` hook runs when our component renders
   * It will return a result object which will contain 3 properties: `loading`, `error`, and `data`
   * Out of the box `Apollo Client` will track errors and loading states for you, which can be rendered by accessing the `loading` and `error` properties.
   * Once data is returned from our query it will be accessible via the `data` property, which we are in turn console logging.
3. Updated the App component to render the `Countries` component.
   * Later we will use this component to render our data in the client.

Save this code and check out the console. And bingo bango!! We have converted our vanilla JS code to function within a React app.

#### Rendering Data - We Do
Our final step will be to render this data with a react component so that a front end user would be able to see it. We just need to make one slight tweak to our code. Go head and replace your current `Countries` component with the code sample below:

```jsx
function Countries() {
  const { loading, error, data } = useQuery(getUsers)

  if (loading) return <p>Loading....</p>
  if (error) return <p>Error....</p>

  return data.countries.map((country, i) => (
    <div key={i}>
      <p>{country.name}: {country.emoji}</p>
    </div>
  ))
}
```
The breakdown:
1. We replaced our initial `console log` return statement for a `map` method. This should look very familiar from our previous React unit. But here is a quick refresher on what we did:
2. We check to see if the `loading` property evaluates as true
   * If it does we return a `p` tag that says `Loading....`
     * Why would we want to do this?
3. Then we check to see if the `error` property evaluates as true
   * If it does we return a `p` tag that says `Error....`
     * Why would we want to do this?
4. If our proceeding two conditions fail that means our data has been queried and returned so we then map over each instance and render a separate  `div` which renders each countries name and flag emoji.

Now if you save and checkout your application in the browser you will see that our data is rendering.


### Rendering Fetched GraphQL Data in React - You Do
Now I want you to give this a shot. Complete the following:
1. Query the `countries` type for two more fields, one of those fields should be a nested field.
   * Be sure to check the `GraphQL Playground Docs` if you are unsure of what other fields are available.
2. Create a second separate query
   * Again, check the `GraphQL Playground Docs` if you are unsure what other queries are able to be handled

### GraphQL Variables
Will explain GraphQL variables and how they provide a better way to set up dynamic values in operations

* This section will have a `I Do` and `We Do`

#### Lab: Write a Lab
Plan to use [Challenge Template](https://git.generalassemb.ly/wdi-dc-instructors/homework-template)
Ideas for first lab:
  1. Provide students a link to a free public GraphQL API and have them query for specific data based on provided prompts.
  2. Provide students a link to a free public GraphqL API and matching REST API and have them query both APIs for the same data based on provided prompts.
      * This will allow then to see the benefits of querying a GraphQL API vs a REST API.
  3. Open to suggestions.

#### Homework: Write a Homework
Plan to use [Challenge Template](https://git.generalassemb.ly/wdi-dc-instructors/homework-template)

Ideas for first Homework:
1. Not sure if I should mimic lesson here? Would really love feedback on what Zakk might like to see here.

#### Additional Resources

- Any useful links should be included in the talk material where the link is first referenced.
- Additional links for further study or exploration are appropriate in this section.
- Links to important parts of documentation not covered during the talk, or tools tangentially used but not part of the focus of the talk, are also appropriate.
