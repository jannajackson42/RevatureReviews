# Week 1 Review

# JavaScript
- High Level Programming language
    - Automatic memory mangagment
    - Cannot do low level things like pointers, or free up memory, or specifc data structres
- Orginally designed as the programming language in Web Browsers
- Brendan Eich designed it in 9 days
    - Has a lot of quirky design decisions
- JS was designed with ***Flexiblity*** as it's guiding principle
    - Python *Readable*
    - Java *Scalable*
    - Scala *Scalable*
- **ECMA**
    - European Computer Manufacturer's Associates
        - Empty acronym
    - They are in charge of JS standards
        - They do not write JS itself they define EcmaScript which JS is an implmentation of
- **JIT** Just in time compiled language
    - JS code is read and then immediately executed by the runtime environment
    - **interpreted**
        - Read and executed line by line
        - Generally less efficient then a compiled language
            - JS
            - Python
            - Ruby
    - **Compiled**
        - Read the ENTIRE program code
        - Generate an executable optimized for that machine
            - C
            - Rust
            - Java
## Syntatical features of JS

### Loosely/dynamicly Typed language
    - No need to declare the type of the variable
```JavaScript
let x = 100;
let y = "Hello"
```
- Weakly Typed Language
    - Variables will have their types implcitly coerced
```JavaScript
const sum = true + true + true; // 3
```

### Scopes

- Scopes in JS
    - Global
        - No keyword (almost always avoid)
    - Function
        - var (always avoid)
    - Local
        - let
        - const
- Scopes are defined using keywords

```JavaScript
function a(){

    var x = 100;// function scoped

    if(true){
        let y = 50;// block scope
    }

    z = 10;// global
}
```

### Data Types
- 7 primitives in JS
```JavaScript

    const num = 10// number
    const name = "adam"// string
    const n = null;// null
    const u = undefined // undefined
    const b = true;// boolean
    // symbol
    // bigInt
```
- Primtives in JS ARE objects
- Primitive is a semantic term in JS

### Type Coercion
- JS has extremely aggressive type coercion
    - Follows from the weak typing
- JS will coerce values into other types ALL of the time

#### Truthy Falsy
- How JS coerces data into boolean values
- There are 6 FALSY values
- Everything else is truthy
- All Falsy values imply nothingness
```JavaScript
null
0
""
undefined
false
NaN
```
- Loose Equality
    - ==
    - Will perform type coercion
- Strict Equality
    - ===
    - will not perform type coercion

### JS Fancy Syntax

#### Object Deconstruction
```JavaScript
const adam = {fname:"adam", lname:"Ranieri", age:19}
const {fname, lname}  = adam
// equivalent to 
const fname = adam.fname
const lname = adam.lname;
```

#### Array Deconstruction
```JavaScript
const ssbu = ["Bowser", "link"]
const [bowser, link] = ssbu;
// equivalent to
const bowser = ssbu[0]
const link = ssbu[1]
```

### Spread Operator
```JavaScript
const ssbu = ["Bowser", "Link", "Pit"];
const streetFighters = ["Ken", "Ryu", "Bison"];
const fighters = [...ssbu, ...streetFighters];

const location = {state:'wv', town:"morgantown"};
const trainerDeatils = {fname:'adam', lname:'ranieri', age:19};
const adam = {...location,...trainerDeatils};
```

### Template Literal
```JavaScript
function greetPerson(person, age){
    console.log(`hello ${person} you are ${Math.round(age)} years old`);
}
```

### Default Parameters
```JavaScript
function subtract(num1 , num2 = 0){
    return num1 - num2;
}
```

### Arrow Functions
- Arrow functions are an alternate syntax for more succint function declarations
    - Especially for anonymous functions
    - the 'this' keyword does work different
    - constantly bound to the same refernce and declaration
- Golden Rule
    - If you have a function that wants to use the this keyword, you want a function not arrow function
```JavaScript

function add(num1, num2){
    return num1 + num2;
}
// the same as
let subtract = (num1, num2) => num1 - num2;
let diff = subtract(7,5)

// VERY JS
let isEven = n => n%2 === 0;

```
### Enhanced Object Literals
```JavaScript
const ryan = {
    fname:"Ryan",
    sayHello(){
        console.log('Helly my name is ' + this.fname);
    }
}
```

### Guards
- JavaScript && and || are not your typical and and ors from other langugaes
- They Select the truthy value
```JavaScript
    const x = "" || "hello";
    console.log(x)// hello
```

### Switch 
```JavaScript

const x  = 10;

switch(x){
    case 10 : {block of code}
    case 12 : {block of code}
    default : {block of code}
}

```

### Enhanced For loops
```JavaScript
const ssbu = ["Bowser", "link", "sammus", "joker", "dark pit"];

// traditional for loop
for(let i = 0; i < ssbu.length; i++){
    const fighter = ssbu[i];
    console.log(fighter)
}

// "for of" loop convienient syntax for the above
for(const fighter of ssbu){
    console.log(fighter)
}

//"for in" loop is for OBJECT PROPERITES NOT ARRAYS
const postage = {sender:"Adam", recipient:"Ryan", address:"Morgantown West Virginia"};

for(const key in postage){
    console.log(key); // way to loop over the keys in an object
}
```
## OOP in JS
- JavaScript is a cake-salad of programming paradigms
- JS does support some aspects of OOP
    - **Prototypal** inheritance
        - An objects directly references another object
    - **Classes**
        - ES6 feature
        - Essentially just an alternate syntax for some nested functions
- most objects in JS are created via object literal syntax
```JavaScript
// key:value pairs. each pair is called a property
const postage = {sender:"Adam", recipient:"Ryan", address:"Morgantown West Virginia"};
```
- Constructor functions are a way to create a template object 
    - Not as common now that Classes in JS

## Functional Programming in JS
- JS is a very functional programming language
- Functional Terminology
    - **First Class Functions**
        - A function IS an object 
        - Functions can be stored in varaibles and passed around in the program
        - Functions are dynamic and can be created at runtime.
    - **Callback Function**
        - A function is passed as a **argument** to another function
        - Ubiquitous in JS
    - **Higher Order Function**
        - A function that takes in a callback function
    - **Anonymous Function**
        - A function defined *on the spot* that has no name
        - Very common with callbacks
    - **Closure**
        - A function returned from another function maintains the reference to a variable defined in the outer function

## Errors
- In JS Errors can be anything
    - You can throw a number, or a string, anything and it generates an error
- JS has only runtime errors
    - No checked exceptions
    - No way to see if a function might throw an error
- There is an Error class 
    - A utility rather than an established standard or offical Error handling hierarchy
- Errors exist to provide the programmers information when things fail
    - Where it went wrong
        - Stack Trace
    - What went wrong
        - message attached to the error object
    - Possible Solutions
        - message attached to the error object
- Keywords
    - try 
        - A block of code you are trying to execute but might throw an error
    - catch
        - A block of code that is called if an error is thrown
    - throw 
        - creating an error
        - immediately stops execution and is caught at the nearest catch block
    - finally
        - block of code at the end of a try catch that always executes
```JavaScript
function validUsername(username = ''){
    if(username.length <6){
        const error = new InvalidUsernameError(`username was of length ${username.length} but must be at least 6 character long`, "try adding numbers at the end")
        throw error// by throwing we are FORCING the developer to deal with the failure
    }
    if(username.includes('!') || username.includes(';')){
        throw new InvalidUsernameError(`username included an invalid character. Invalid characters are ! ;`, "avoid special chracters")
    }
    return {status:"success"};
}

try {
    const isValid = validUsername('hank95');
    console.log(isValid)
} catch (error) {
    console.log('The user tried to create a username but failed beacuse ' + error.message)
    console.log("Possible solution " + error.solution)
}finally{
    console.log('block of code that will always execute')
}
```

## TypeScript
- A superset of JavaScript
    - Any valid JS is valid TS
- TypeScript supports features JS does not
    - Static typing 
        - optional in TS
    - Generics for arrays
    - More OOP support
        - Access modifiers for properties of a class
        - Shorthand syntax for classes
        - interfaces 
            - A list of properties the object must have
- Configurable language
    - **tsconfig.json**
        - A configuration file for any TS in a folder
        - Can be used to make your TS as strict or as lenient as you want
- You cannot directly execute TS files 
    - TS must be **transpiled** into JS first
    - You can choose how this transpilation occurs
        - what verion of ES
- TS-Node
    - It is a very helpful NPM install 
    - Transpiles TS into JS as it runs
        - IT still goes through that process of transpiling it just does it under the hood

## Node.js
- It is a runtime environment for JS.
- It is used to run JS applications outside of the browser.
    - It was not the first to run JS outside of the browser
    - It was the first one that was good.
- Ryan Dahl from google create it
- ***NPM*** node package manager
- The build tool and dependecy manager for node.js applications
- It is also a repository of JavaScript libraries
- ***package.json***
    - The core configuration file of any node project
    - depenencies
        - what outside JS libraries you incorporated
    - Author
    - License
    - Description
```bash
    npm install somepackage
    npm init 
```
# Web Servers and HTTP
- The best program in the world means nothing unless people have some way to communicate with it.
    - Desktop Application which uses a Graphical User Interace
    - A console applications that just prints to the terminal and people type into it
    - ***Web Servers*** are programs/appplications that can take in inupts via HTTP.

## HTTP
- HTTP **Hyper Text Transfer Protocol**
- It is a request response based protocol.
    - A user/client makes an **HTTP Request** 
    - The server/web-server responds with an **HTTP Response**
    - Every Request is guaranteed to generate a response
- Web Servers and HTTP are supposed to be Language Agnostic
    - The client does NOT need to know what programming language the server is written

## Anatomy of an HTTP or HTTP(S) Request and Response
- **Request**
    - URL
        - Uniform Resource Locator
        - The address of where to send the Request
    - Verb
        - The type of HTTP Request it is
            - GET - (*usually* for retrieving information)
            - POST
            - PUT
            - DELETE
            - PATCH
    - Headers
        - Key value pairs that contain meta-data on the request
            - The content-type (image, text, JSON, etc...)
            - Authorization (specific Key necessary for security)
    - Body
        - Main content of a request
        - OPTIONAL
            - Requests do not NEED to send content
- **Response**
    - Status Code
        - a number indicator how the request was processed
        - 100's information
        - 200's success
        - 300's redirects
        - 400's client error
            - 403 client does not have appropriate access
            - 404 client requested a URL that does not exist
            - 451 Unavailable for legal reasons
        - 500's (server error)
    - Body
        - OPTIONAL
        - content
    - Headers
        - key value pairs

## Express
- Express is a micro-framework for creating web-servers in node
- Very popular.
- Route Handling
    - app.httpVerb("/uri", handlerFunction)
```TypeScript
app.get("/hello", (req, res)=>{
    res.send("Hello Everybody");  
});

app.get('/greet/:fname', (req,res)=>{
    const name: string = req.params.fname;
    res.send(`Great to meet you ${name}`);
});
```
- Express Middleware
    - Term somewhat invented by Express
```TypeScript
app.use(express.json());// middleware is code that will be applied to all routes
// the software is in the middle of a client making an http request and your code that handles that http request
```
# Week 3 Review
- Client Side Technology
    - Your browser
- Key components of a web browser
    - HTML/CSS renderer
    - JS Engine
    - HTTP Client (way to make http Requests)
## Pillars of Clientside
- Three core technologies make up client side development
    1. HTML
        - Hyper Text Markup Language
        - Content and structure
    2. CSS
        - Cascading Style Sheets
        - Style
    3. JS
        - JavaScript
        - Make web pages dynamic
            - Manipulate the DOM
            - Make AJAX requests
### HTML
- HyperText Markup Languague
- NOT a programming language
- Core building block of HTML is the **Element** or **Tag**
- Tags can contain conent in the middle
- Tags can have attributes that add additional info or funtionality to that tag
```html
    <p id="example"> Hi I am a simple tag</p>
```
- Syntax of HTML
    - All tags should be closed at some point
    - Some tags are **self-closing**
        - img
        - hr
    - Do not have Overlapping Tags
```html
    <!-- Over lapping tags -->
    <p> My name is Adam <b>Ranieri</p></b>
```
- Minimum tags for an HTML page
```html
<!Doctype html>
<html>
    <head></head>
    <body></body>
</html>
```
Important tags
    - html
        - Root tag
    - head
        - meta information about the file
    - body
        - content of the web page
    - link
        - refences css files outside of the web page
    - script
        - including JS in your web page

### CSS
- Cascading Style Sheets
- Adds style to your web page
- **Domain Specific Language** DSL
    - A lanuguage designed to do one thing
- ***Cascade Algorithm***
    - Many styles can be applied to the same element
    - The Algorithm determines what styles override other styles
    - *the most specific style for an element wins*
- CSS Sytnax
    - **Rule**
        - Selector + Declaration
    - **Selectors**
        - To what html element(s) does this css rule apply
            - Tag
            - id
            - class
    - **Delaration**
        - The style to apply
    - **Properties**
        - The individual pairs of stylistic attributes
```CSS
    /* tag selector */
    p {color: red} 
    
    /* class selector */
    .intro {color: green}

    /* id selector */
    #bio {color: yellow}
```
![CSS Rule](https://puzzleweb.ru/en/images/css/1_1.png)

### DOM
- Document Object Model
- A tree structure of html nodes
![DOM](https://www.w3schools.com/js/pic_htmltree.gif)
- JS was orginally designed to manipulate the DOM
    - Add elements
    - Remove elements
    - Edit elements 
```html
<button onclick="someFunction()"> </button>
```
- Event Listeners
    - Setting up 'traps' on elements 
    - Will execute the function when the event is triggered

```JS
const element = document.getElementById("someElement");
element.addEventListner("click", () => {
    // something to execute when the event occurs
})
```

### AJAX
- Asynchronous JavaScript and XML
- JS to make http requests in the backgroud of a browser
- This IO operation is inherently asynchronous 
    - based on promises
- **XmlHttpRequest**
    - This is an object used by JS to perform AJAX
- **fetch**
    - Is an API supported by browsers that allows JS to make AJAX requests
    - Under the hood it uses an XmlHttpRequest object
        - Using fetch you never directly interact with it
```JS
async function getData(){

    const options = {
        method:"POST",
        body: JSON.stringify(associate),
        headers:{
            'Content-Type':"application/json"
        }
    }

    const response = await fetch("http://something.com/data", options);
    const body = await response.json()
}
```
# Week 4 Review

## React
- Front-end JS/TS framework 
- Created by Facebookx
- **Virtual DOM**
    - Under the hood how React works
    - Creating, updating garbage collecting JS objects is really fast for a browser to process
    - Constantly re-rendering and directly ediing nodes on the DOM is *not* efficient for a browser to perform
    - React has a virual dom consisting of JS objects that it tracks
        - It uses the virtual DOM to make **surgical** efficient updates to the real DOM
- **Single Page Application**
    - The entire website is all on one html page
    - JS is used to update and edit the single page
- Architecture of React
    - **Components**
        - Core building blocks of a React web page
        - Modular chunks of HTML/CSS/JS
        - Written in **JSX**
        - Two Varities
            - Class based
            - Function Based
                - Newer
                - *Preferrable* - Adam's opinion
    - **JSX**
        - JavaScript Extension
        - Hybrid language of HTML/CSS/JS
        - React philosophy is that these language *should* blend together
    - React does not enforce a specific style or organization when building an application
        - for better or for worse
    - A React application is essentially a Gigantic function composed of many smaller functions
- Component Anatomy
    - **props**
        - An object that holds variables passed in from the parent
    - **hooks**
        - functions that *hook* into the component to give it extra abilities
```JSX

// a component must start with a capital letter
export default function EmployeeRow(props){ // it can take in props to which can be used in the component

// must return a single root JSX tag
    return(<>
    </>)

}
```
- React Design Philosophy
    - Write as many *pure* and *stateless* components as possible
        - Components that do not have an internal state
        - They can take in props but there is no value being updated within them
    - Data only flows *down* in a react application
        - From parent to child via props
        - The only way for a child to update a parent is to pass *down* a setter function as props
        - **Display**
            - Statless components that are designed to look nice and display something
        - **Container**
            - stateful components that will pass data into display components
    - State in React is immutable
        - You have to replace rather than update stateful values
        - Derived from a functional perspective that a pure function has no side-effects and thus no mutability

## Hooks

### In Built React Hooks
- useState()
    - Creates a stateful encapsulated value within a component
    - returns and array with 2 values in it
        1. A read only variable
        2. Setter function that will update that variable and re-render the component
```JSX
const [employee,setEmployee] = useState()
```
- useRef()
    - create a constant reference to an HTML element
    - Primary use case is to get information out of inputs
```JSX
const nameInput = useRef()
```
- useEffect()
    - Gets its name from the term **side Effect**
        - Programming term for code that mutates values or edit information from Outside of a function
    - useEffect allows you to execute a callback function at given points in the component lifecycle
```JSX
useEffect(()=>{},[]) // execute the callback function ONCE when the component is first loaded
useEffect(()=>{})// execute anytime a stateful value changes
useEffect(()=>{},[somethinStaeful])// execute only when that specic state changes
useEffect(()=>{
    return ()=>{
        // yet another callback
    }
})// execute the returned callback when the component is destroyed
```
- useContext()
    - Allows a component to access a context object
    - Can be helpful for retrieving values from a parent component *without* having to use props
```JSX
const guestContext = createContext({fname:"Adam",lname:"Ranieri"})

export default function GuestInfo(){
    const guest = useContext(guestContext)
    guest.fname
}
```

## Redux
- Third party library for state management in React
- Redux vs Redux Toolkit
    - Redux original library and core code
    - Redux Toolkit is a developer friendly software package
        - Has a nice API and helpful methods
        - More specifically designed to work well with React

- Redux design pattern
![Redux Deisgn](redux.png)
- Data only flows in one way
- This data flow is circular
- Key Terms
    - **Store**
        - An encapsulated state to be used by your application
    - **Reducers**
        - Functions that can edit/update the state/store
    - **useSelector**
        - A hook that allows you to retrieve informaton from the store
    - **useDispatch**
        - A hook that allows you to send an action to a reducer
    - **Action**
        - A Object that has a these two properties {type:"Groceries/addProduct", payload:"Eggs"}
            - payload is optional

## React Router v6
- One library for performing routing in React
- Key Components
    - BrowserRouter
        - All routes go inside the BrowserRouter
    - Route
        - Defines a path along with the element to connect to
    - Routes
        - Defines a group of routes
    - Link
        - Equivalent to an anchor tag

# React Native
- A platform for writing native software
    - mobile devices like Android or IOS
    - rarer but possible, apple watch or tv app
- The main drivers behind React Native
    - Companies wanted to leverage their web developers to build these applications
    - Developers wanted to leverage their current skill set and popular libraries
        - JavaScript
        - You could use just about any node package
- You cannot port a React app to React Native
    - "Learn Once Write Anywhere"
- React Native borrows its core design from React

## Core Components 
- React Native does not have HTML
    - View
        - A rectangle block of Screen
    - ScrollableView
        - A view which you can scroll
    - Text
    - Button
    - Switch
    - FlatList
    - DetailList
    - Image
- Much limited selection than React
- CSS does not exist 100% in React Native
    - All styles must be applied in JS
        - Hope you like flexbox
    - Not all CSS features are available
- AsyncStorage
    - ReactNative version of LocalStorage
    - Slighly different implementation
- Some web browser functions do have a React Native API corollary
    - alert()
- Other React Native APIs are helpful for specific phone related features
    - Dimesions.get()
    - Platform.OS
    - PanResponder



## Expo
- A framework for building React Native applications
```bash
expo init
expo install
```
- expo install and other CLI commands can automatically link native modules (Android or IOS specific software) to your JS code

# Week 6 Review

# Server and Serverless

- Any deployed backend/web server hast to ultimately be running on a server somewhere in the world
- A phycical a machine that you own
- A virtual machine provisioned from a cloud provier

## Server
- **Infrastructure as a Service**
    -  A cloud offering that gives the developer essentially virtual hardware
        - Examples
            - Azure Virtual Machine
            - Azure Disk (The hard drive associated with a virtual machine)
- Advantages
    - High level of control of your resource/server
        - Get an exact operating System
        - Specific hardware stats
        - Intsall proprietary/custom programs
- Disadvantges
    - A lot more effort to set up rather than serverless
    - A lot more maitnence than serverless
    - Often more expensive than serverless
        - Serverless offering tend to dynamically scale to meet demand
        - Often charge you by the minute

## Serverless
- **Platform as a Service**
    - A cloud offering that give the developer a base to build off of
    - The platform just requires the source code a bit of configuration
- Advantages
    - Faster to develop and deploy
    - Developer friendly
    - Often cheaper 
    - More optimized/auto scaling usage
- Disadvantages
    - Lose fine grain control of the application
    - You have to adhere to rules set by that platform
    - Persistent data stored with the application *can* be more difficult
        - Saving data to an external database is the ideal
- Most serverless apps strive to *stateless* 
    - Do not rely on in memory sessions
    - Do not rely on local files
    - **REST** is a stateless architecture

# Linux
- The most common operating system for Web Server
    - Advantages
        - Huge Developer Community
        - Lightweight 
            - No bloatware slowing down your application
        - Most are open source
            - Usually a good thing for security
            - Any security threats are noticed by the community at large very quickly
        - In-built package managers
            - Allows for quickly installing software
                - yum
                - apt
    - Disadvantages
        - Not beginner friendly
        - No graphical component in most distros
            - People like graphics
- Unix
    - The first really popular OS
        - Not popular anymore because it is not free
    - From the 70's when most people did not have their own computer
    - Most computing was done on a single maingrame where multiple actives users used the machine at once
        - This origin is part of the reason why changing permisssions and root user sudo access is so prevalent in linux

## Common Linux commands
```bash

pwd # print working directory
ls # list show what files and folders are in the current directory
touch # creates a file
clear # removes text from screen
ps # used to list all running processes on the computer
top # show running processes
kill # to terminate a process
disown # to disconnect a process from the users terminal
& # run a process in the background
man # manual
cat # print out contents of a file

# making and moving files
touch # make a file
mv # move
cp # copy past
rm # remove
mkdir # making a directory

# Root User
sudo # super user do


## Text Editors in most linux distros
nano # bad
vim # extra bad (there is too much vim hate)

```

## XSS
- Cross Site Scripting
- A security vulnerability where external JS is executed on the browser
    - That JS could be used to get sensitive information from local storage or cookies
        

# Week 7 Review

## React Native
# Essential Terminology
- Native
    - inherent to the device the code is running on.
        - example: Java code in Android OS for operating the camera
- Native Module
    - Code written in Java/C/Swift/etc that directly interacts with the native phone APIS.
- JSI
    - JavaScript Interface
    - Allows JavaScript methods to directly use methods/objects in a Native Module

# Essential Components
- Core Components provided by react Native
- Will be turned into Native versions on phone or other device

|Component|HTML Equivalent|Usage|
|---------|---------------|-----|
|View| div| a rectangular pactch of screen|
|Text| p, h1-h6, b | Any text that needs to be displayed|
|Image| img| display an image|
|ScrollView| div | A scrollable view|
|TextInput| input type="text"| allows for text input|
|FlatList| ul | Simple List of rendered views|
|SectionList| dl | List of rendered views with a title for each item|
|Button| button| button for handling presses|
|Pressable| N/A| Wrapper for other components to add press functionality (Replaces Touchable Opacity)|
|Switch| input type="checkbox"| Boolean value input|
|StatusBar| N/A | Shows Celluar, battery etc...|

# React Native APIs
- React Native provides APIs for common operations on a phone
- These APIs are accessible by your React Native Code
    - Avaialable as imports from react-native

|API|Usage|
|---|-----|
|Animated| Performs smooth animations|
|Platform| Used to get the OS the code is running on like Android, web or IOS|
|Vibration| Virbate the phone|
|useWindowDimension| API in the form of a hook that allows getting screen size|
|StyleSheet| Used to write styles in a CSS-esque syntax|
- Many more not listed

# Styling
- True CSS does not exist in React Native
    - CSS is for a web browser not phone
- Using the StyleSheet API you can create CSS-esque styling using object-literals in code
- The core method of styling is flexbox

| Property      | Values          | Description                                         |
| ------------- | --------------- | --------------------------------------------------- |
| flexDirection | 'column', 'row' | Used to specify if elements will be aligned vertically or horizontally |
| justifyContent| 'center','flex-start','flex-end','space-around','space-between'| Used to determine how should elements be distributed inside the container |
| alignItems    | 'center','flex-start','flex-end','stretched' | Used to determine how should elements be distributed inside the container along the secondary axis (opposite of flexDirection) |

# SQL
- **Structured Query language**
    - The scripting language used for **RDBMS**
- **RDBMS**
    - Relational Database Managament System
        - Postgres
        - MySQL
        - MariaDB
- Relational Database
    - Stores infromation in tables
    - These Tables are often **normalized** and *reference* each other
- **Schema**
    - Overal design of a database
        - Tables, columns and how they are connected
        - Any constratints/foreign keys
        - Any user restrictions
- Sub languages of SQL
    - **DDL**
        - Data Definition Language
        - Used to create,alter or drop tables and constraints
            - CREATE, DROP, ALTER
    - **DQL**
        - Data Query Language
        - Used to query information
            - SELECT
    - **DML**
        - Data Manipulation Language
        - Used to edit data within a table
            - insert, update, delete
    - **TCL**
        - Transaction Control Language
        - Commands for transactions
            - COMMIT, ROLLBACK
    - **DCL**
        - Data Control Language
        - Commands for editing and granting access to the the database
            - Could be used to make a table read-only or grant a user permission to only insert into a table
            - GRANT, REVOKE
- **Constraints**
    - **Primary Key**
        - Marks the column as unique and not null.
        - This is the main way to identify a record
    - CHECK
    - NOT NULL
    - UNIQUE
    - DEFAULT
    - **Foreign Key**
        - Marks the column as referning a value in another table
        - The value MUST exist in the other table
        - prevents **Orphan Records**
            - Records that refernce a record in another table that does not exist.
        - **Child Table**
            - Table that has the foreign key constraint.
        - **Parent Table**
            - Table that holds the record the foreign key refers to.
- **Nomralization**
    - The elimination of redundant data in a database.
    - Storing infromation in many tables that refernce each other as oppsed to embdded data.
    - Normalization IS NOT inherently better.
    - **1nf**
        - Every record record in a table has a primary key 
        - Data in a column should be atomic
            - No array like information
            - Data cannot be meaningfully broken down into more fields
                - full_name is not atomic => first_name, last_name
    - **2nf**
        - be in 1nf
        - No **functional dependencies**
        - shooting_percentage is a functional dependency
            - It is a value that could be calculated using other field

    - **3nf**
        - be in **2nf**
        - no **Transitive Dependenies**
        - inlcude data in a table that could be found in another table
        - team_name is a transitive dependency
            - You could use the team_id to look at the team table and found out any information about the team

#### Functional Dependency
|player_id|shots_attempted|shots_made|shooting_percentage|
|---------|---------------|----------|-------------------|
|101|200|60|30|
|101|1000|150|15|

#### Transitive Dependency
|player_id|shots_attempted|shots_made|team_id|team_name|
|---------|---------------|----------|-------|---------|
|101|200|60|1|Monstars|
|101|1000|150|1|Monstars|

- **Transactions**
    - The base unit of database editing
    - Any updates to a database are done in a *transaction*
    - ACID properites of transaction
        - **Atomic** *all or nothing*
            - Either every statement has to work for it to be commited
                - 3/3 => all statements will be committed
            - If a single statement does not work *nothing* is commited
                - 2/3 => no records being commited
        - **Consistent**
            - Database moves only via transactions from one consistent state to another
            - There is no midway commit point in a transaction where half the statements are commited and the other half need to be processed
        - **Isolated**
            - In reality multiple transaction started by different clients/users could be working in parallel on your database.
            - The RDBMS will have isolation levels when processing transactions to prevent inconsistent phenomena
            - In short, if you have mulitple transactions running at once, you can have inconsistencies in reading the database
        - **Durable**
            - Any failures in a transactions are handled gracefully.
            - No corrupted data or data loss.

# SQL vs NoSQL 
- One is not better than the other
- Depends on the Application

|Database Type|Data Model|Consistency|Transactions|Schema|
|-------------|----------|-----------|------------|------|
|SQL|Relational|ACID|Fully Supported|Rigid/Well Defined|
|NoSQL|Document/nested embedded objects|BASE| Sometimes Supported|Flexible/ not enforced|
- **BASE**
    - **B**asically **A**vailable **S**oft State  **E**ventual Consistency
    - Consistnency model where data is NOT always in the most up to date consistent matter.
    
## Azure Resources
- **Resource Group**
    - A logical collection of resources.
    - Does nothing by itself
    - Usually you would have a resource group for a single app
        - Put all the resources for one app in a single resource group

|Resource Name|Type|Management|.. as a Service|
|-------------|----|------|---------------|
|Azure Virtual Machine|Computing|Server Based| Infrastructure|
|Azure Disk|Storage|Server Based| Infrastructure|
|App Service|Computing|Serverless| Platform|
|Azure Functions|Computing|Serverless| Platform|
|CosmosDB| Database| Serverless|Platform|
|Postgres SQL Server| Database| Server Based| Infrastructure|
|Stroage Account| Storage| Serverless| Platform|
|Static Web App| Hosting| Serverless| Platform|
|Outlook|Email|Serverless|Software|
|Office 365| Prodcutivity Suite| Serverless| Software|
|Teams | Team Managment| Serverless| Software|

## Scaling Web Resources
- **Vertical Scaling**
    - Getting a larger machine to handle more traffic
- **Horizontal Scaling**
    - Add more machine machines and spread traffic between them
    - Usually preferred for Web Apps
        - Pros
            - If one VM fails not all users are impacted
            - Most web apps are not computationally or memory intensive
        - Cons
            - harder to set up
            - State withing a web server it is more difficult
![Scaling](scaling.png)

## Sonar Cloud
- **Static Code Analysis** Tool
- Allows you to hook a GitHub repo to sonar cloud and have sonar cloud lint your code.
- It will highlight potential issues in the code
    - Code Smells
    - Best Practices
    - Possible Security Threats

## Azure Functions
- Servlerlss Offering by Azure
- Allows for quickly deploying a snippet of code
- **Trigger**
    - Something that causes your function to run
        - examples
        - HTTP Request
        - CosmosDB action (upsert or deletion)
        - Uploading to a storage account
- **Authorization**
    - Security for a functions
        - Anonymous
            - Anyone could invoke the function
        - API Key
            - Anyone with the API key could invoke the function
        - Admin
            - Only someone logged in as an Admin could invoke the function
- **Glue Code**
    - Code that knits your many applications and web services together
    - Examples
        - Filters the JSON from an endpoint to be more helpful to a frontend
        - Function that records whenever a record was deleted in CosmosDB
        - Function that allows uploading uploading a file to a Storage Account


# Week 8 Review

# Microservices
- Pioneered by Netflix
- Development paradigm of splitting the backend into many smaller services/servers
- These servers are often responsible for a single small part of the application
    - REST API for a specific resource
    - Server that provides that authentication
    - Service that uploads photos
- Creates an ecosystem of APIs 
- Pros
    - Small applications are easier to write
    - A backend could be written in many different languages
    - You scale services individually in the cloud for max effiency
    - A single service failing does not mean the entire backend crashes
    - Makes your backend APIs more modular and easy to expand on
- Cons
    - **Discovery Problem**
        - tons of softare out there to try and solve the problem
            - Zuul
            - Zookeep
            - Ribbon
        - How do know the endpoints and IP addresses of all these APIs
            - IP addresses in the cloud are often ephemeral
                - updated and deleted often
        - Solutions
            - Registry Services
                - When a service comes online it logs itself in a registry 
                - You check the registry to find the service
                    - Can be done manualy or programmatically
    - Add more latency
        - A lot more HTTP requests
    - More configuration from developers
            

## Monolith
- In a monolith architecture all the backend for an applicaiton is in single program
    - Could be a large Java application
    - Could be a larg Node applicaiton
- Benefits
    - Some applications are easier to design when they are all one program
        - Maybe they have to ue the same local files
        - The developers have a lot of expericence in that langauge or backend framework
- Drawbacks
    - Monoliths can be difficult to work on
        - The code base could be massive, hundreds of source code files
        - Intimidating to add new features or developers
    - Locks you in to particular langauge/framework for an application
    - Do not scale very well
        - Most applications have code/features that get used much more than others
            - Login vs view reimbursemts

### Microservice vs Monilith neither is inherently better

|Comparison|Monolith|Microservices|
|----------|--------|-------------|
|Setup|faster and easier| More complex setup|
|Scaling| Vertical Scaling| Horizontal Scaling|
|App size| Large| Small code size|
|Latency|  Small | HTTP everywhere increases latency|
|Cloud Focus| Originate from on premise(often in the cloud now)| Shine in cloud environments|



# Docker
- The problem 
    - ***Well it works on my machine***
    - Deploying back-ends/applications is difficult
        - Applications have a lot of requirements to run
            - Specific environment variables
            - Specific file structure for your app to use
            - Specific runtime
                - node.js
                    - maybe node 14 not node 6
                - python
            - Computers have different operating systems
            - Starting an app require knowledge of the application
                - node npm start or ts-node or 
                - python3 py
                - ruby
                - Execute the command in the correct directory
            - You have to know what port your application is listening on 
- Solutions
    - deal with it
        - Makes deployment difficult
        - you get a virtual machine spend hours configuring it
    - Serverless options
        - All serverless options have their own learning curve
            - constantly forgetting GCP vs Azure vs AWS configurations and UI
        - Serverless options give you less control of the application
            - Might have to have a specific file structure
            - Run a specific runtime
    - **Containerize** The docker solution
        - Build a virtual environment for your application
        - Ship your application in a virtual environment
- Docker
    - Is **containerization software**
    - Put applications into easily distrubutable formats
- Docker Circle of life
    1. **Dockerfile**
        - A script that will generate an image
    2. **Image**
        - A blue print for a container
        - Class
    3. **Container**
        - Instance of an image
        - Object
- Dockerhub
    - Github for Docker images
    - You can find an image of almost anything on Dockerhub
![Docker Circle of Life](dockercircleoflife.png)
```bash
docker build . -t greeting-app
# docker build dirctoryofdockerfile -tag nameofimage

docker run -p 4000:3000 greeting-app
# docker run -port outsideport:containerport image
# Create a runnning instance of the image AKA a container

docker kill 17108hdje # container id

docker ps # view all running containers

```
## Container vs VM
- VM Virtual Machine
    - A heavyweight virtualization option
    - It has its own Operating System
    - Has its own memory CPU and hard drive
    - **Azure Virtual Machine**
- Container 
    - Lightweight virtualization
    - They run on top of an Operating system
        - Usually linux for docker
    - They are just a linux process
    - More like a **running application** on a machine
        - Having excel open
        - Having a desktop app running

![Container vs VM](https://images.contentstack.io/v3/assets/blt300387d93dabf50e/bltb6200bc085503718/5e1f209a63d1b6503160c6d5/containers-vs-virtual-machines.jpg)

### Best practicies for containers
- usually a container should have only 1 running application inside of it
- Containers are good for *stateless* applications
    - Containers ephemeral 
        - Any data inside a container is lost forever when killed
    - You can persist data if you use a volume and mount it to the container
        - A diskspace allocated to a container

### Kubernetes K8s
- Container Orchestration Managment Software
    - Allows you to run dozens to thousands of containers with dynamic auto-scaling and rounting
    - Runs of a cluster of vms
- Docker Swarm is an alternative to K8s (Not as popular), less advanced but easier


### Azure Resources 
- **Azure Container instances**
    - Resource for deploying containers
    - Uses a shared pool of RAM and CPU to run your containers
- **Azure Active Directory**
    - Authentication is hard
    - Creating users and getting users logged in is very common for web apps
        - The process to be secure
    - People often forget their username or password
    - One user usually uses multiple web apps
        - You want to keep track of them
        - You only want certain people to be able to login or have certain permissions
    - Outsource authentication to Microsoft
        - **Tenants**
            - Phonebooks of users
        - **User**
            - A uniquely identifiable person
        - **redirectURI**
            - the route that **MSAL** Microsoft Authentication library will redirect after login
            - make sure the URI is whitelisted in Active Directory
    - You can NEVER put sensitive information in a frontend
- **API Management**
    - API management tool
    - A wrapper around any of our deplpyed APIS
        - Give a uniform domain name
        - Authentication
        - Editing requests and responses before getting to the server 
        - Validate JSONs
        - etc...
    - How it applies to microservices
        - Makes much easier to uninfy and standardized the many APIS     