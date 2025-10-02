#coding #webdev 
NodeJS is a [[Java Scripts]] Event Driven runtime which allows one to run java script without the requirement of browser.

#### Steps to Write a backend server (Building a basic [Nginx](https://nginx.org/) server)
Nginx is an open-source software used as a high-performance web server, reverse proxy, load balancer, mail proxy, and HTTP cache.
	 `You Wont get VS Code Autocompletes while using Bun it only works for nodejs and npm`

```js
const fs = require("fs"); // This is used for reading and writing to files
const path = require("path"); // This is used for handleing paths and extnetions.
const http = require("http"); // This is used to build a basic hhtp server.

const port = 8000; // This is a virtual port that the server listens to

const server = http.createServer((req, res) => {

// The createSever() provides 2 args request and response

const filePath = path.join(__dirname,req.url === "/" ? "index.html" : req.url); // This line returns the complete absolute path to the index.html file if the requested url is

const fileExt = String(path.extname(filePath)).toLowerCase();
const mimeTypes = {
// Mimes are files types that nodejs or libuv support and are able to parse.
".html": "text/html",".css": "text/css",".js": "text/javascript",
};

const contentType = mimeTypes[fileExt] || "application/octet-stream"; // octet-stream is a generic binary file

fs.readFile(filePath, (err, content) => {

if (err) {
console.log(`Error: ${err}`)

}} else {
res.writeHead(200, { "Content-Type": contentType });
res.end(content, "utf-8");}});});

server.listen(port, () => {
console.log(`Server listening at port ${port}`);
});
```



### Notes
- `process.argv` is a very helpful method that fetches all the extra parameters passed through during run time. This can be used to create CLI (Command Line Interface) to for [[Unix]] or other OS to handle arguments passed in when running a command. It returns a list of all the args passed starting from "node env", "file_name" and then the rest.
- `http` is used to create and manage server of the backend, A server is created using `http.createServer()`
- under the hood `libuv` is responsible to bind all the requests and responses, as base JS cant listen to https servers.
- `__dirname` return the absolute path of the current directory and `__filename` returns the absolute path of the current file name.
- An `request/response` must and will contain 2 types the `HEAD` and the `BODY`. The HEAD generally contains the meta data of the file like, [statusCode](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Status) etc and the BODY contains the actual content of the file.