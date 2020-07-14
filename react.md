### React

```js
// a person component that shows person's name
function Person(props){
    return <div style = {{fontSize: props.age}}>
        {props.name}
    </div>
}
```

### use a component
```js
//render the person component
// and pass in the name "Alice" in a prop
<Person name = "Alice" age={30}>
```

### Looping over components, using .map()
```js
function App(){
    const people=["Alice","Bob","Casey","Diana"]
    return <div>
        {people.map((item,index)=> {
            return <Person key = {index} name = {item}/>
        })}
    </div>
}
```

### useState
```js
//"state" lets you handle changes on your site in an intelligent way
functin Counter(){
    const [count,setCount] = useState(0)
    return <button onclick = {() => setCount(count+1)}>
        You clicked me {count} times!
    </button>
}
```

### conditionally rendering components
```js
//use && to render a component based on some javascript condition
funtion App(){
    return <div>
        {1+1===2 && <WillRender />}
        {1+1===3 && <WontRender />}
    </div>
}

funtion App(){
    return <div>
        {1+1===2 ? <WillRender /> : <WontRender/>}
    </div>
}
```

### useEffect
```js
function App(){
    useEffect (()=>{
        //run code once on startup
    }, [])
}
```

**or use useEffect more dynamically**
```js
function Person(props){
    useEffect (()=>{
        //this code run EVERY time that the person's age changes
    }, [props.age])
}
```



