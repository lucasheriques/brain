Example API: https://snowtooth.moonhighway.com
# Queries
We use it when we are requesting data from an API. When sending a **query**, you ask for units of data by **field**. The fields we ask will be the ones coming in the JSON response.

```graphql
query {
  allLifts {
    name
    status
  }
}
```

The **query** keyword is the **operation name**. It describes the type of query or operation that we are sending to the GraphQL service. Nested inside the curly braces are the **fields**, and inside the next pair is the **selection set**.

It's possible to add multiple queries to a document, but only one operation is allowed per request.

# Connections
In a GraphQL query, a field can return either scalar types or object types.

GraphQL has five built-in scalar types: `Int`, `Float`, `String`, `Boolean` and `ID` (which is a unique identifier String).

GraphQL object types are groups of one or more fields defined in the schema. They define the shape of the JSON object that will be returned.

We can connect objects together by querying one object for details about related objects.

```graphql
query {
  allLifts {
    name
    capacity
    trailAccess {
      name
    }
  }
}
```