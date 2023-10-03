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

#### promises

```
promise
  .then((result) => { ··· })
  .catch((error) => { ··· })
  .finally(() => {
    /*logic independent of success/error */
  })

  <!-- function parameter
   -->
   function greet({ name, greeting }) {
  console.log(`${greeting}, ${name}!`)
}

greet({ name: 'Larry', greeting: 'Ahoy' })


```

#### destructing assignment

```
const [first, last] = ['Nikola', 'Tesla']

let {title, author} = {
  title: 'The Silkworm',
  author: 'R. Galbraith'
}
```

#### spead operator

```
const users = [
  ...admins,
  ...editors,
  'rstacruz'
]

const options = {
  ...defaults,
  visible: true
}
```

## Async/await

async is used in conjuection with a function declaration creates an async functino that returnes a promises. async functnios allow us to use the keyword await to block the event loop

## setInterval and setTimeout

**setInterval** executes a code block at a specified interval in millieseconds. it requires two paramters. simply it will execute the code every millieseconds interval
**setTimeout** executes a code block once after milleseconds given parameter

## JSON

JSON is javascript object notation is a format usually used for sending and recevieng the data between frontend and backend.

### JSON syntax

```
{
  "student": {
    "name": "Rumaisa Mahoney",
    "age": 30,
    "fullTime": true,
    "languages": [ "JavaScript", "HTML", "CSS" ],
    "GPA": 3.9,
    "favoriteSubject": null
  }
}
```

**Note the following syntax rules for JSON:**

- The curly braces, {..}, hold objects.
- The square brackets, [..], hold arrays.
- Every name-value pair is separated from another pair by a comma, ,. Similarly, every item in an array is delimited by a comma as well. Trailing commas are forbidden.
- JSON property names must be in double-quoted (" ") text even though JavaScript names do not hold by this stringency.

## glosarium

- _web server_ merupakan sebuah komputer yang berjalan. yang memproses
  request yang datang. dan memberikan responses
- _client_ is a software that request the data to the server (could be browser or mobile device, etc)
- _web api_ is a set of rules and protocols that allows different software applications to communicate and interact with each other over the internet
- _database_ is a place to storedata, could be relational or nosql
