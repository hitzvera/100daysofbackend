# what is a backend

a backend is a process to response client request

## how the big picture the application work

so the big picture of the application works is like this
we have a different entity (could be more).

1. client
2. application server
3. web server
4. web api
5. database

6. client is requesting to the web server some data to process
7. the webserver is processing the request by communicating by the application server
8. the application server (nodejs) is find the right response to the database through web api (get, post, put, delete).
9. the database takes the data, and sent to the client.

## reminder of javascript

### ES6

#### let, const

let is mutable and const is immutable.

#### template strings

```
const message = `Hello ${name}`

<!-- multiline string -->
const str = `
hello
world
`
```

## glosarium

- _web server_ merupakan sebuah komputer yang berjalan. yang memproses
  request yang datang. dan memberikan responses
- _client_ is a software that request the data to the server (could be browser or mobile device, etc)
- _web api_ is a set of rules and protocols that allows different software applications to communicate and interact with each other over the internet
- _database_ is a place to storedata, could be relational or nosql
