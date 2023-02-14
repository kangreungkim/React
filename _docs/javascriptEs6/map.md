---
title: ES6/map
tags: 
 - javascript for
 - javascript map 
description: 
---

# ES5 - For

```
         for(let i=0; i<json.length; i++){
             var data = json[i]
             var idx = i+1
             result.push(      
                 <tr className="hidden_type">
                     <td>{data.MODEL_NM}</td>
                     <td>{data.SERIAL_NO}</td>
                 </tr>
             )
         }
         return result
```

## ES6 - Map

```
        const listItems = json.map((data, idx)=>{
            let keyRow = `data ${idx}`;
            result.push(
                <tr className="hidden_type" key={keyRow}>
                    <td>{data.MODEL_NM}</td>
                    <td>{data.SERIAL_NO}</td>
                </tr>
            )
        });
```