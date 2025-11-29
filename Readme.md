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

## step by step example of us-mecontext 
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

## constrolled component and uncontrolled component in react 
what are controlled and uncontroleld component ?
in react , forms input (like input>, <textarea>,<select>) can be handled in two ways:
constrolled components: react control the value 
uncontrolled components : DOM controls the value 

##  1. controlled components :
a controlled component is a form input whose value is controlled by react state.
the input value always comes from state .
every input change triggers setState/useState
single source of truth ; react 

example controlled components:
import React,{useState} from 'react";
function ControlledForm(){
    const [name,setName]=useState("");
    const handlechange=(e)=>{
        setName(e.target.value);
    };
    return (
        <div>
        <h2>Controlled component</h2>
        <input
        type="text"
        value={name}
        onChange={handleChange}>/>
        <p>value:{name}</p>
        </div>
    );
}
export default ControlledForm;

## 2. uncontrolled components:
an uncontrolled component is a form input whose value is handled by the DOM, not by the react.
react does not track the value 
you use refs to access the value 
input manages its own state inside browser 

example : uncontrolled components:
import React,{useRef} from 'react";
function UncontrolledForm(){
    const inputRef=useRef(null);
    const handleSubmit=()=>{
        alert("value:"+inputRef.curent.value);
    };
    return (
        <div>
        <h2>Uncontrolled component</h2>
        <input type="text"
        ref={inputRef}/>
        <button onclick={handleSubmit}>Show Value,?button>
        </div>

    );
}
export default UncontrolledForm;

### what is context api in react ?
context api is a built in react feature that lets you share values across the component tree without passing props through every intermidiate level (avoid props drilling) typical uses : theme , auth / user info , locale , app setting , etc.

Quick summary:

context provides a way to pass data through the component tree without manually passing props at every level , use React.createContext() to create a context , wrap parts of the tree with <Provider value={...}> and consume with useContext() or Context.Consumer

### minimal example (single file, functional , recommended pattern )
import React,{createContext,useState,useContext} from "react";
import {createRoot} from "react-dom/client";
//1: create context
const ThemeContext=createContext();
//2: provide component
function ThemeProvider({children}){
    const [theme,setTheme]=useState("light");
    const toggle=()=>settheme(t=>(t==="light"?"dark":"light"));
    //useMemo could be used here if value is expensive or contains function 
    const value={theme,toggle};
    return(
        <ThemeContext.Provider value={value}>
        {children}
        </ThemeContext.Provider>
    );
}
//3; consume via useContext
function themeBox(){
    const {theme}=useContext(ThemeContext);
    const style={
        padding:"20px",
        borderRadius:"8px",
        background:theme==="light"?"#fff":"#222",
        color:theme==="light"?"#000":"#fff",
        textAlign:"center",
    };
    return <div style={style}>Current time:{theme}</div>;
}
function ThemeToggle(){
    const {toggle}=useContext(ThemeContext);
    return <button onClick={toggle}>Toggle theme</button>;
}
function App(){
    return (
        <ThemeProvider>
        <h1>Context API Exampe</h1>
        <ThemeBox/>
        <ThemeToggle/>
        </ThemeProvider>
    );
}
createRoot(document.getElementById("root")).render(<App/>);

## useReducer in react 
useReducer is a react hook used to manage complex state logic 
it is an alternative to useState, espacially when :
state updates depend on the previous state ,
you have multiplle related state variable 
or you want redux style state management at com-onent level 

is work using :
1. state -> the current state 
2. dispatch (action): function used to update state 
3. reducer(state,action): pure function that returns the new state 

basic syntex :
const [state,dispatch]=useReducer(reducer,initialState);

simple example :
import React,{useReducer} from "react";
function reducer(state,action){
    switch(action.type){
        case "increment":
            return {count: state.count +1}
        case "decrement":
         return {count:state.count-1};
        default:
            return state;
    }
}
export default function Counter(){
    const [state,dispatch]=useReducer(reducer,{count:0});
    return(
        <div>
        <p>Count: {state.count}</p>
        <button onClick={()=>dispatch({type:'increment'})}>+</button>
        <button onClick={()=>dispatch({type:'decrement'})}>-</button>
        </div>
    );
}

## why use useReducer instead of useState
when satuation is simple use useState
when satuation is complex state(object , nested ) then use usereducer 
and when satuation is multipe state updates in one action then use usereducer 
and when satuation is predictable state transition (redux like) then use useReducer 
when updates depend on previous state both (but usereducer is cleaner)

### example managing a form using useReducer 
using useState for forms get messy , useReducer keeps it clean 

const initialState={
    name:"",
    email:"",
    age:""
};

function reducer(state,action){
    return{
        ...state,
        [action.field]:action.value
    };
}

export  default function Form(){
    const [state,dispatch]=useReducer(reducer,initialState);
    return(
        <div>
        <input
        name="name"
        value={state.name}
        onChnage={(e)=>dispatch({field:e.target.name,value:e.target.value})}/>
        <input 
        name="email"
        value={state.email}
        onChnage={(e)=>{
            dispatch({field:e.target.name,value;e.target.value})
        }}/>

        <input 
        name="age"
        value={state.age}
        onChange={(e)=>dispatch({field:e.target.name,value:e.target.value})}/>
        
    )
}

