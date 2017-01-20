Facebook invented it. Github is using it, and so are these companies. So why are these big companies using GraphQL? And why is changing the face of Web services? Today I will introduce you to GraphQL, talk about its history, and how it can make writing your next API a breeze.

First does anyone know what API stands for? Application programming interface - don't worry even if I had to google that. In an online API, it is simply a way to access information from the WebServer. So for example if you want to handle credit card payments you do not have to code the entire process yourself, Stripe does that for you. Emails? Mailgun. You might be familiar with this one. APIs power the ever interconnected World wide web.

GraphQL is a query language for APIs. In the simplest form. It can be looked at as SQL queries, but it is not a database. In fact, GraphQL doesn't care where you get the data. That way, you specify your sources, in memory, SQL databases, No-SQL databases, even from another API.

So to give you a taste of GraphQL, this is what a query for a Github user and his or her first 3 organisations looks like
```GraphQL
{
  viewer {
    login
    bio
    organizations(first: 3) {
      edges {
        org:node {
          name
        }
      }
    }
  }
}
```

So why prefer GraphQL over REST, which has been around for 17 years?
There are 3 big benefits.

Let's go back to the query. One user's login handle, the user's bio, and three organisation's name.
In github's rest API, you would have to first call the endpoint once for the user, then again for the organisation names.

With GraphQL, you only ever have to do one.

Alright, so maybe 2 to one query isn't that much. Let's look at the first query for the user. We only get their login handle and their bio. Github generously returns us all these:
```JSON
{
  "login": "octocat",
  "id": 1,
  "avatar_url": "https://github.com/images/error/octocat_happy.gif",
  "gravatar_id": "",
  "url": "https://api.github.com/users/octocat",
  "html_url": "https://github.com/octocat",
  "followers_url": "https://api.github.com/users/octocat/followers",
  "following_url": "https://api.github.com/users/octocat/following{/other_user}",
  "gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
  "starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
  "subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
  "organizations_url": "https://api.github.com/users/octocat/orgs",
  "repos_url": "https://api.github.com/users/octocat/repos",
  "events_url": "https://api.github.com/users/octocat/events{/privacy}",
  "received_events_url": "https://api.github.com/users/octocat/received_events",
  "type": "User",
  "site_admin": false,
  "name": "monalisa octocat",
  "company": "GitHub",
  "blog": "https://github.com/blog",
  "location": "San Francisco",
  "email": "octocat@github.com",
  "hireable": false,
  "bio": "There once was...",
  "public_repos": 2,
  "public_gists": 1,
  "followers": 20,
  "following": 0,
  "created_at": "2008-01-14T04:33:35Z",
  "updated_at": "2008-01-14T04:33:35Z"
}
```

Maybe that's fine for one user, but let's say you want to query many users' bio. Which, Github's multiple user query doesn't provide. That's a lot of wasted bandwidth and data. If you're doing it all on the phone, your users will cry when they see their data bills. GraphQL has an aim of reducing data usage, so your users can have really bad internet and still browse.

Lastly, the greatest benefit is the type system. Ever wanted the safety of a type system? If the API has really bad documentation, do you know if "followers" will return you the count, list of names or a list of uers? With GraphQL, you can guarantee that the object you get back is definitely of that type.

So all these benefits explain why big companies are using GraphQL, but what is in for us, people who build small projects? We, who don't have audiences in Congo using their 2G internet.

I'll show you right [now](https://developer.github.com/early-access/graphql/explorer/).

In short, GraphQL meets the new demographics who are getting introduced to the internet, and at the same time, provides a great development experience. This is an introduction to GraphQL and I hope it has sparked some thoughts of adopting it. Thank you.
