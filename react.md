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

### useRef
```js
function App(){
    const divRef = useRef()
    useEffect(()=>{
        divRef.current.focus()
    },[])
    return <input ref={divRef}
        placeholder="hello world"
    />
}
```

### animations with React
```js
function TextInput({show}){
  const [width] = useState(Math.random()*300)
  const inputRef = useRef()
  useEffect(()=>{
    if(show) {
      setTimeout(()=> inputRef.current.focus(), 250)
    }
    else inputRef.current.blur()
  }, [show])
  return <input ref={inputRef} 
    placeholder="hello world"
    style={{
      width: width,
      transition: 'all 0.2s',
      transform: show ? 
        'translate(0,0) rotate(0)' : 
        'translate(400px,0) rotate(180deg)',
      opacity: show ? 1 : 0,
    }}
  />
}
```

### Example App
```js
import React, {useState, useEffect} from 'react';
import './App.css';

const counterz=[{
  label:'Add One', n:1, initial:5
},{
  label:'Minus Two', n:-2
},{
  label:'Add 100', n:100
}]

function App() {
  return (
    <div className="App">
      {counterz.map((c,i)=>{
        return <Counter key={i} // React needs a "key"
          label={c.label} n={c.n} initial={c.initial}
        />
      })}
    </div>
  )
}

function Counter(props){
  const {label, n, initial} = props
  const [count, setCount] = useState(initial||0)
  return <div style={{marginTop:25}}>
    <button onClick={()=> setCount(count+n)}>
      {label}
    </button>
    <div>
      {count}
    </div>
  </div>
}

export default App;
```



