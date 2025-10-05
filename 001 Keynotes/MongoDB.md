#coding #webdev #database

[MongoDB](https://www.mongodb.com/) is a NoSQL (Not only SQL) database for full stack application. Any back-end dosent directly talk to the database, it has a middle layer (generally for [mongoDB](https://mongoosejs.com/) its ).

Mongoose is an ODM/ORM (Object Document Mapper/Object Relational Mapper) which acts as an additional layer that helps one connect with mongoDB in a much easier manner.

### How to setup MongoDB / Mongoose (Via MongoDB atlas)
- Install mongoose via `npm install mongoose`.
- Next in your `.env` file create a path to the mongoDB url and create a new file in `db` directory to access and connect to the database. (Here is a sample code)
```js
import mongoose from "mongoose";
export default const connectDB = async () => {

try {
await mongoose.connect(process.env.MONGO_URl)
console.log("Mongoose Connceted");

}catch(error) {
console.error("Mongo connection error: ",error)
process.exit(1) // Quits the process if there is an error
}}
```
-  Setting up the database in [Atlas](https://cloud.mongodb.com/). On the home page of Atlas go to `network access` tab and (**ONLY FOR TESTING**) give access to everyone for read and write. 
- Then head to the `database access` tab and get the `username` and `password` to connect to the database.
- Now head to the main page and click connect on your cluster. Select `compass`, copy the url and paste it into the `.env` file. Change the username and password with respective values.
### Mongoose
- Next step is to create a schema using Mongoose as validator :
```js
import mongoose, {Schema} from "mongoose";

const userSchema = Schema({
// Your Schema Here
}, {
timestamps: true // Adds 2 new fields appCreated and appStopped
})
export const User = mongoose.model("User", userSchema)
```
- Mongoose gives very good schema validation:
	1. The default syntax is: `<field-name>: {<property1>,<prop2>,...}`
- Next are hooks, they run some functionality before (pre), or after (post) some action is performed on the schema / database.
```js
userSchema.pre("<action>", function(next){
// Your 
// funtionality
})
```
- the `this.Modified("<field>")` is used to check if the field if modified and then execute some functionality.
- Next are methods: They are checkers that run code using the schema's data. 
```js
userSchema.methods.methodName = function(args) {
// Functionality
}
```
- 