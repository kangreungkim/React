---
title: react-route-dom
tags: 
 - BrowserRouter
 - Routes
 - Route
 - Link
 - NaviLink
 - Outlet 
description: 
---

# react-route-dom

> 이 문서는 react-route-dom 6.8.1 기준으로 작성됩니다.

1. 설치
`npm install react-router-dom`

2.  파일및 폴더 구조

    1.src>>index.js

    ```javascript
    import React from 'react';
    import ReactDOM from 'react-dom/client';
    import Router from './router';

    const root = ReactDOM.createRoot(document.getElementById('root'));
    root.render(
        <React.StrictMode>
            <Router />
        </React.StrictMode>
    );
    ```

    2.src>>router.js

    ```javascript
    import App from './component/App'
    import NavRestApi from "./component/NavRestApi";
    import NavWebsocktApi from "./component/NavWebsocketApi";

    import {BrowserRouter, Routes, Route} from "react-router-dom"

    export default function Router(){
        return(
            <BrowserRouter>
                <Routes>
                    <Route path="/" element={<App />}>
                        <Route path="rest-api" element={<NavRestApi />} />
                        <Route path="websocket-api" element={<NavWebsocktApi />} />
                    </Route>
                </Routes>
            </BrowserRouter>
        )
    }
    ```

    - 2.소스에서 `<Route path="/" element={<App />}>` 코드서 Tag를 닫지 않았다. Tag를 닫은면 `</ Outlet>` Tag가 작동하지 않는다.


    3.src>>component>>App.js

    ```javascript
    import { NavLink, Outlet } from "react-router-dom";
    import navStyle from "./navStyle";

    function App() {
    return (
        <>
        <h1>Upbit REST및 WebSocket 사용 test</h1>
        <nav>
            [ <NavLink to="rest-api" style={navStyle}> REST API Example </NavLink> ]
            [ <NavLink to="websocket-api" style={navStyle}> WEBSOCKET API Example </NavLink> ]
        </nav>
        <hr />
        <Outlet />
        </>
    );
    }

    export default App;

    ```

    4.src>component>NavRestApi.js

    ```javascript
    import { memo } from "react";
    import { NavLink, Outlet } from "react-router-dom";

    function NavRestApi(){
        return(
            <>
                <h3>Rest 예제입니다.</h3>
                <hr />          
            </>
            
        )
    }

    // export default NavRestApi
    export default memo(NavRestApi);
    ```

> react-router-dom 에서 BrowserRouter, Routes, Route , NaviLink, Outlet 사용하는 예시입니다.