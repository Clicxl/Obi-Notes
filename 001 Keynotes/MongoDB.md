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