---
title: Provider/Consumer
tags: 
 - Context
 - Provider
 - Consumer
 - useState
 - useContext
description: 
---

# 카운터 증가 예입니다.

context.js
```
import React from "react";

const Context = React.createContext(null);
export default Context;
```

index.js
```
import React from 'react';
import ReactDOM from 'react-dom/client';
import Counter from './counter';

const root = ReactDOM.createRoot(document.getElementById('root'));

root.render(
    <Counter />
);
```
counter.js
```
import React, {useState} from "react";
import Context from './context'
import Button1 from "./button1";
import Button2 from "./button2";

function Counter(){

    const [count, setCount] = useState(0);
    const [vals, setVal] = useState(
        {name:'영선', count:100}
    );

    function changeCount(){
        setVal(
            {name : vals.name, count: vals.count + 1}
        );

        setCount(prev_count=>prev_count+1);
    };

    function changeName(){
        const val = vals.name=="영선"?"병찬":"영선"
        setVal(
            {name : val, count: vals.count}
        );
    };

    const store = {
        first :{key: count, func:changeCount, setFunc:setCount},
        second:{key: vals, func:changeName, setFunc:setVal}        
    }

    return (
        <Context.Provider value={store}>
        <div>
          <p>You clicked {vals.count} / {vals.name}</p>
          <Button1 /><br />
          <Button2 />
        </div>
        </Context.Provider>        
      );    
}

export default Counter;
```

button1.js
```
import React, {Component} from "react";
import Context from './context'

function Button1(){
    const vals = React.useContext(Context);

    function changeSetCount(){

        vals.first.setFunc(prev_count=>prev_count+1);
    };
        
    function changeCount(){

        vals.first.func();
    };

    return(
        <>
            <button onClick={() => changeCount()}> 카운터 증가+{vals.first.key}</button><br />
            <button onClick={() => changeSetCount()}> 카운터 증가+{vals.first.key}</button>

        </>
    );
}

export default Button1;
```
button2.js
```
import React, {Component} from "react";
import Context from "./context";

function Button2(){
    const vals = React.useContext(Context);

    function changeName(){

        vals.second.func();
    };

    return(
        <>
            <button onClick={() => changeName()}> 이름 변경</button>
        </>
    )
}

export default Button2;
```




