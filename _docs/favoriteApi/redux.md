---
title: redux
tags: 
 - redux
 - react-redux
description: 
---

# redux로 구현한 카운터 증가 예입니다.

src >> index.js
```
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';

const root = ReactDOM.createRoot(document.getElementById('root'));

root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```
src >> App.js
```
import React from 'react';
import { Provider } from 'react-redux';
import store from './redux/store';
import TwoContainer from './components/TwoContainer';
import FiveContainer from './components/FiveContainer';

function App() {
  return (
	<Provider store={store}>
		<div>
			<TwoContainer />
			<br />
			<FiveContainer />
		</div>
	</Provider>	
  );
}

export default App;
```

src >> components >> FiveContainer.js
```
import React from 'react';
import { connect } from 'react-redux';
import { multiplyFive } from '../redux';

function FiveContainer(props){
	return (
		<div className='FiveContainer'>
			<h1>{props.val_five}</h1>
			<h3>Click the button to multiply the above number by 5</h3>
			<button onClick={props.multiplyFive}>Multiply by 5</button>
		</div>
	);
}

const mapStateToProps = state => {
	return {
		val_five: state.five.val_five
	}
}


const mapDispatchToProps = dispatch => {
	return {
		multiplyFive: () => dispatch(multiplyFive())
	}
}

export default connect(
	mapStateToProps,
	mapDispatchToProps
)(FiveContainer);
```
src >> components >> TwoContainer.js
```
import React from 'react';
import { connect } from 'react-redux';
import { multiplyTwo } from '../redux';

function TwoContainer(props){
	return (
		<div className='TwoContainer'>
			<h1>{props.val_two}</h1>
			<h3>Click the button to multiply the above number by 2</h3>
			<button onClick={props.multiplyTwo}>Multiply by 2</button>
		</div>
	);
}

const mapStateToProps = state => {
	return {
		val_two: state.two.val_two
	}
}


const mapDispatchToProps = dispatch => {
	return {
		multiplyTwo: () => dispatch(multiplyTwo())
	}
}

export default connect(
	mapStateToProps,
	mapDispatchToProps
)(TwoContainer);
```

src >> redux >> store.js
```
import { createStore } from 'redux';
import rootReducer from './rootReducer';

const store = createStore(rootReducer);

export default store;
```

src >> redux >> rootReducer.js
```
import { combineReducers } from 'redux';
import TwoReducer from './multiply_two/TwoReducer';
import FiveReducer from './multiply_five/FiveReducer';


const rootReducer = combineReducers({
	two: TwoReducer,
	five: FiveReducer
})

export default rootReducer;
```

src >> redux >> index.js

```
export { multiplyTwo } from './multiply_two/TwoAction';
export { multiplyFive } from './multiply_five/FiveAction';
```

src >> redux >> multiply_two>> TwoAction.js
```
import { MULTIPLY_TWO } from './TwoType';

export const multiplyTwo = () => {
	return {
		type: MULTIPLY_TWO
	}
}
```

src >> redux >> multiply_two>> TwoReducer.js

```
import { MULTIPLY_TWO } from './TwoType';

const initialState = {
	val_two: 1
}

const TwoReducer = (state = initialState, action) => {
	switch(action.type){
		case MULTIPLY_TWO: return {
			...state,
			val_two: state.val_two * 2
		}
		
		default: return state
	}
}

export default TwoReducer;
```

src >> redux >> multiply_two>> TwoType.js
```
export const MULTIPLY_TWO = 'MULTIPLY_TWO';
```

src >> redux >> multiply_five >> FiveAction.js
```
import { MULTIPLY_FIVE } from './FiveType';

export const multiplyFive = () => {
	return {
		type: MULTIPLY_FIVE
	}
}
```

src >> redux >> multiply_five >> FiveReducers.js
```
import { MULTIPLY_FIVE } from './FiveType';

const initialState = {
	val_five: 1
}

const FiveReducer = (state = initialState, action) => {
	switch(action.type){
		case MULTIPLY_FIVE: return {
			...state,
			val_five: state.val_five * 5
		}
		
		default: return state
	}
}

export default FiveReducer;
```

src >> redux >> multiply_five >> FiveType.js
```
export const MULTIPLY_FIVE = 'MULTIPLY_FIVE';
```


