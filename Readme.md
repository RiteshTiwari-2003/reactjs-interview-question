# REACT INTERVIEW IMPORTENT QUESTION

# 1. can you tell me what is the difference between state and props

so whenever you building a react application you have to build in component inside the react
this small small component have to manage data, inside the component we use state,
and props is something which component recieved

# how will you create new peoject by the way

so basically there are multiple way to create project
one is you can just create a new create react app, so create react app is package which helps you build a new project in react

# so what is the role of react in software development ?

a client when sent the request to the server then thaqt request first hit the ui server , this ui server also called frontend server , clientt server , this frontend server will have all the static html content in itself and like name of the website and othr static content but
for dynamic content like the list of order the ui server will send the request to some api server this api server can also called middleware and it is only responsible for business logic and getting and posting the data only there will not be any ui element like html,
css javascript, in this api server now whether you want to get post or update the data your ui server call the api server and this api server will then get insert or update the data inside the databse server both this api server and database server also called as backend

in case of get database will respond back some data to the api and then api will do some logic inside it like sorting and filtering and then finally send the data to the client which will display the data to the browser or you can say the user this is the basic flow now

for database we use sql as language for running script and sql server or oracle as the dbms we will use
similarly for backend c sharp java pfp as a language and the frameworksare dotenet spring or laravel arrival okay

why we need dbms and framework
because dbms simplify the complex database operation and server side framework simplifies the complex server side programing

similarly for frontend we need html css javascript as a language but simplify the complex ui building we use react which is javascript library
we also use anguler which is a framework

react is used to simplifyt he creation of complex ui application

# what is react ?

we know react is the open source javascript library ,react is used for what ,react is used for building user interface ,

why we need react when already have html css and javascript
this is most imortent point we need react because react simplifies the creation of single page application by using reusable components that is the answer of this question

# what is the single page application?

first see web page structure here we have main component if any component is updated or a new component is added the page will never reload or refreahed ok only the same page is updated every that is called sigle page application
now if i go to the bowser to show you see for example if you search youtube and in youtube you see whatever i do on the page the whole page never reload becaquse youtube is the single page application above you cansee it never refresh only the component inside the youtube are loading but not the whole page , this is the single page application, now if i open some other application which is not a single page and have multiple pages

# how to start and create a projext?

in vs code in new terminal first write npx create-react-app <folder-name>
after this go in that folder using : cd <folder-name>
and run npm start
start is a script in package.json file

### what are hooks in react?
hooks are spacial function in react that let functional components use state , lifecycle features and other react capabilities without writting a class.

hooks are introduced in react 16.8 to replace many repetitive class component patterns 

before hooks: only class component could use state and lifecycle 
after hook : functional component can do everything 

### useContext in react 
useContext is a hook that allows you to access data from context without needing to pass props manually through every component called props drilling.
iyt helps when you need to share data like:
theme (light/dark mode)
user info(logged in user)
language 
global setting 
auth token 

## interview definition 
the usecontext hook lets you access values from react context directly inside functional component , without passing props through intermidiate component .

### why use useContext?
without context -> you pass props through 4 - 5 layer even if middle component dont need them .
with context-> any component can get the value directly 

## step by step example of udecontext 
we need 3 steps :
1. create a context 
2. wrap your app with the provider 
3. use useContext inside child component 

step 1: create a context 
import {createContext} from "react";
export const ThemeContext=createContext();

step 2: wrap with provider (usually in app.js):
import React,{useState} from "react";
import {ThemeContext} from "./ThemeContext";

function App(){
    const [theme,setTheme]=useState("light");
    return(
        <ThemeContext.Provider value={{theme,setTheme}}>
        <Home/>
        </ThemeContext.Provider>
    );
}
export default App;

value hold the data you want to share globally 
any component inside provider can access the context 

step 3: use useContext in a child component 
import React,{useContext} from 'react";
import {ThemeContext} from "./ThemeContext";
function Home(){
    const {theme,setTheme}=useContext(ThemeContext);
    return(
        <div style={{backgroundColor:theme==="light"?"#fff":"#333",
        color:theme==="light"?"#000":"#fff",
        padding:"20px",}}>
        <h1> current Theme: {theme}</h1>
        <button onClick={()=>setTheme(theme==="light"?"dark":"light")}>
        Toggle team 
        </button>
        </div>
    );
}
export default Home;
