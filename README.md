# rails-graphql

## Installation

Install dependencies:

```
bundle install

rails db:setup
```

Starting the server:

```
rails server
```

Opening the application:

```
open http://localhost:3000/
```

## Sample GraphQL Queries

List first 10 links, containing "example":

```graphql
{
  allLinks(first: 10, filter: {descriptionContains: "example"}) {
    id
    url
    description
    createdAt
    postedBy {
      id
      name
    }
  }
}

```

Creates new user:

```graphql
mutation {
  createUser(
    name: "Radoslav Stankov",
    authProvider: {
      email: { email: "rado@example.com", password: "123456" }
    }
  ) {
    id
    email
    name
  }
}
```

Creates new user token:

```graphql
mutation {
  signinUser(email: {email: "rado@example.com", password: "123456"}) {
    token
    user {
      id
      email
      name
    }
  }
}
```

Creates new link:

```graphql
mutation {
  createLink(url:"http://example.com", description:"Example") {
    id
    url
    description
    postedBy {
      id
      name
    }
  }
}
```

Creates new vote:

```graphql
mutation {
  createVote(linkId:"TGluay0yMQ==") {
    user {
      id
      name
    }
    link {
      id
      url
      description
    }
  }
}
```
