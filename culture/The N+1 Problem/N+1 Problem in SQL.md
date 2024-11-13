[source](https://youtu.be/qPfAQY_RahA?feature=shared)
#database #sqlite #performance
Usually happens when using tools like ORM or GraphQL with Client/Server based databases.
```js
books = db.books.all().limit(20) // #1
for (book of books) {
	reviews = book.reviews().limit(5) // #2
}
```

Here, we recognize that the query #2 gets executed once for each books we've queried in #1. Here is the ==N+1 Problem==

## What's the problem ?
Individuals queries are more expensive in all the popular databases except for SQLite.
![[single queries chart.png]]

The time taken to process a query can be separated in 3 parts :
- CPU Time
- Disk IO
- Network IO, represents more than 90% of the time
The only way to avoid this unavoidable latency from the network would be to use an embedded database such as SQLite. 
Actually, the queries take the same amount of time, but since SQLite avoids Network IO duration it avoids the N+1 problem.
