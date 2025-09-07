#coding 
This is a detailed explanation of how to build a full stack project. This uses the MERN (MangoDB, Express, React, [[NodeJS]]) stack using [[Java Scripts]] but one can use any other stack or these steps can be followed into any project architecture.

### Prerequisites to building a Full Stack Project:
- First before the frontend or backend the PRD (Project Requirement Document) is created to note down all the stuff to build, and where to stop the project at. It answers questions like, "Why is this project being built?", "What purpose it servers?", "For whom is it being built?" etc.

```md
## Project Requirement Document (PRD)

### 1. Project Overview
*Product Name*:
*Version*:
*Product Type*: 

**Small description of the project**

### 2. Target Users
**List of prodcut users**

### 3. Core Features
**List of all features in order that the product provides**

### 4. Technical Specification
#### 4.1 API Endpoints Structure
#### 4.2 Permission Matrix (If Required or If Auth based system)
#### 4.3 Data Models

### 5. Security Features (If Required)

### 6. File Managememt
```
### Project Setup 
- If using nodeJS or npm run `npm init` and setup the workspace.
- This is where all is scripts like `npm run dev` lie, we can add custom scripts to make development easy.
```json
"scripts": {
"dev": "node index.js"
},
```
-  It is generally prefred to use the module type of import `import {} from <module>`, so to set that up the below should be added to the `package.json` below the `main` keyword
```json
  "type": "module",
  ```
- Next step is to setup [prettier](https://prettier.io/) using `npm install --save-dev --save-exact prettier`.
- After this the `.prettierrc` file is created to write down the configs of project and `.pritterignore` file is created just like `.gitignore` to notify prettier from not modifying  unwanted files.
- Next initialise the [[Git]] repository and create a `.gitignore` file, you can use this [website](https://www.toptal.com/developers/gitignore) to automatically produce common ignore files for git. After all this do the first commit.
- Next setup a hot-reload of the server, generally [nodemon](https://www.npmjs.com/package/nodemon) is used to do the hot-reload of the server but a new alternative is `node--watch`.
- Change the `dev` script in package.json to run the program with nodemon instead of node
```json
"dev": "nodemon index.js"
"start": 'node index.js'
```