#webdev #coding 
It is an opinionated web framework built for [[NodeJS]], which handles everything from routing, API handling to all of middle ware components. 
##### Basic Syntax:
```javascript
import express from "express"
APP = express()
```
- To use ports or routing we use the `APP.get("<route>", (req,res) => ())`
```js 
APP.get("/", (req,res) => {
	res.send("Hello User")
})
```
- Here the get method provides 2 args request (req) and response (res) which is fed into an arrow function.
- `res.send()` Methods sends the string to the web server to render.
- It is a opinionated convention to create and send in routes in a separate file called `app.js` which is then imported into the main file
- [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Guides/CORS) (Cross Origin Resource Sharing): It is a mechanism from the backend that shares the domain, scheme, port to the browser for it to allow access to other the server.
- EXPRESS CONFIGURATIONS: (These are some basic starter configs for express)
```js
import cors from "cors"
// Basic Configs
app.use(express.json({limit: "16kb"}))
app.use(express.urlencoded({extended: true, limit: "16kb"}))
app.use(express.static("public"))

// CORS configs
app.use(cors({
origin: process.env.CORS_ORIGIN?.split(",") || "http://localhost:5173",
credentials: true,
methods: ["GET", "POST", "PUT", "PATCH","DELETE", "OPTIONS"],
allowedHeaders: ["Content-Type","Authorization"]
}))
```
- `app.use()` is a method that is used as the middle-ware to communicate between the front-end and back-end.
- `express.json()` allows functionality with json formatting. `limit: "16kb"` sets a limit to how much data can be sent over.
- `express.urlencoded({extended: true})` parses the url_encoded data and makes it available in [[Java Scripts]] with the `req.body` method.
- `express.static(<dir/to/public>)` makes the public folders like images available to use.
-  Next step is to setup Error handling and API response system. The error handling is already done by [[NodeJS]] which provides an `Error` class which we can extend from (The below is a copy-able template so it can be used on any web server)
```js
class APIErrors extends Error { // A class that extends from Nodes error class
constructor(statusCode, message="Some thing went wrong", errors = [], stack =""){

super(message)
this.statusCode = statusCode // The Status code of the response
this.data = data // The data that is being send
this.message = message // Message to be sent
this.errors = errors // An array of errors that can be itirated
this.sucess = false
this.statusCode = this.statusCode > 400

if (stack){ /* Since the stack is not always available we check if it is present if not then we capture it*/ 
this.stack = stack
}else {
Error.captureStackTrace(this,this.constructor)
}
}}
export {APIErrors}
```
- The next part is the API response system which we should build a class for (The below is a copy-able code so it can be repurposed).
```js
class APIResponse {
constructor(statusCode, data, message="Sucess"){

this.statusCode = statusCode
this.data = data
this.message = message
this.success = true
this.statusCode = statusCode < 400
}}
export {APIResponse}
```
- Constants: They are some fixed values like `user permissions` or `task status` that are stored in `utils/constants.js` and are like dictionary and provide key value pair to access these constants. Below is an example:
```js
export const ConstEnum = {
KEY: "value",
}
export const AvailableConstEnum = Object.values(ConstEnum) // Returns a list of all the values in the constant as an array
```
- Next connect your back-end to [[MongoDB]] using anything like mongo-db atlas.