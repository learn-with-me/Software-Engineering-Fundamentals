# GraphQL

Builds declarative API not tied to any language or framework. Puts lesser weight on user's data plan. Capability to fetch the query  in response when sending mutation request. Get real time updates with subscription. Can be available via any network protocol.

Netflix has their own version called Falcor.

**GraphiQL** - An in-browser IDE for writing, validating and testing GraphQL queries.

##### Core Concepts

```
type, query, mutation, subscription, resolver functions, fragment
```

GraphQL server has one resolver function for each field, whose only job is to fetch data for the corresponding field. GraphQL allows clients to ask a server for information about its schema. GraphQL calls this **introspection**.

Relay/Apollo enables you to focus on important part of the application, rather than have to deal with repetitive work. Mainly lets you focus around describing data requirements and display information in the UI.

##### Architectural Use Cases

```
GraphQL server with a connected database
GraphQL server to integrate existing system
A hybrid approach with a connected database and integration of existing system
```

##### Apollo Client

```
Apollo abstracts away all lower-level networking logic and provides a nice interface to the GraphQL server.

Installation
============
$ yarn add apollo-client-preset react-apollo graphql-tag graphql

apollo-client-preset - offers some convenience by bundling several packages you need when working with Apollo Client
    apollo-client
    apollo-cache-inmemory
    apollo-link
    apollo-link-http
react-apollo         - contains the bindings to use Apollo Client with React.
graphql-tag          - GraphQL parser. Every GraphQL operation sent to Apollo Client will be parsed by the gql function
graphql              - contains Facebook’s reference implementation of GraphQL
                       Apollo Client uses some of its functionality as well.


Configuration
=============
```



