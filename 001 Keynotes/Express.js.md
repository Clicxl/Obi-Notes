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
- Now that mongoDB/Atlas is setup, we change the main `index.js` to listen to port only when the DB is responding else throw an error.
```js
connectDB()
.then(() => { // .then() method is used as a try catch
APP.listen(PORT, () => {
console.log(`Proj1 is listening on port https://localhost:${PORT}}`);
})})

.catch((err) => {
console.error("MongoDB connection error: ",err);
process.exit(1)
})
```
- Next are the health-check controllers, these help check if the servers API endpoints are online or not in AWS or Azure.
- So using our old `APIresponse` class we create a new controller.
```js
import { APIResponse } from "../utils/api-response.js"

const healthCheck = async (req, res) => {
try {
res
.status(200).json( // Is response.status code is 200 
new APIResponse(200,{message: "Server is running!"}) // Creates a new and sends response via json format 
)

} catch (error) {
next(error)
}}
export default healthCheck
```
- Next step is to create the routes for this controllers (In this project the route for the healthchecker is `/api/v1/healthcheck`).
```js
import { Router } from "express"; 
import { healthCheck } from "../controllers/healthcheck.controllers.js

const router = Router()
router.route("/").get(healthCheck) // From there all the routes that are diverted here are manager (Like if /api/v1/healthcheck/instagram came up we can add it here)
export default router
```
- Next step is to notify the app of this route (Inject after all the configurations): 
```js 
// Import routes

import healthCheckRouter from "./controllers/healthcheck.controllers.js"
APP.use("/api/v1/healthcheck",healthCheckRouter) // Reroutes all /api/v1/healthcheck into the healthCheckerRouter
```
- A new utility is created to resolve all the requests. It main goal is to convert all the try-catch into a Promise based function.
```js
const asyncHandler = (requrestHandler) => {

return (req,res,next) => { // Returns a function 
Promise
.resolve(requrestHandler(req,res,next))
.catch((err) => next(err)) // Handles the errors and passes it to express error handling
}}
  
export {asyncHandler}
```
- So using this we will change the controller:
```js
const healthCheck = asyncHandler(async (req,res,next) => {

res
.status(200).json(
new APIResponse(200,{message: "✅ Server is running!"})
)})
```
- Next write the schema of the database using [[MongoDB]].
- 