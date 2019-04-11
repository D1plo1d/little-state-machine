# little-state-machine

> Flux state management should be easy

[![Tweet](https://img.shields.io/twitter/url/http/shields.io.svg?style=social)](https://twitter.com/intent/tweet?text=Little-State-Machine&url=https://github.com/bluebill1049/little-state-machine)&nbsp; [![npm downloads](https://img.shields.io/npm/dm/little-state-machine.svg?style=flat-square)](https://www.npmjs.com/package/little-state-machine)
[![npm](https://img.shields.io/npm/dt/little-state-machine.svg?style=flat-square)](https://www.npmjs.com/package/little-state-machine)
[![npm](https://img.shields.io/npm/l/little-state-machine.svg?style=flat-square)](https://www.npmjs.com/package/react-lazyload-image)

- Follow flux application architecture
- Tiny and simple
- Build with React Hook

## Install

    $ npm install little-state-machine

## Usage

app.js
```jsx
import state from './state'
import YourComponent from './yourComponent'
import { StateMachineProvider, createStore } from 'little-state-machine'

createStore({
  state,
});

const App = ({children}) => {
  return <StateMachineProvider
    value={{
      store: globalState,
      updateStore,
    }}
  >
    <YourComponent />
  </StateMachineProvider>
}
```

yourComponent.js
```jsx
import { updateName } from './action.js'
import { useStateMachine } from 'little-state-machine'

export default function YourComponent() {
  const {
    action,
    state: { name },
  } = useStateMachine(updateName);

  return <div onClick={() => action('bill')}>
    {name}
  </div>
}
```

state.js
```js
export default {
  name: 'test',
}
```

action.js
```js
export function updateName(state, payload) {
  return {
    ...state,
    name: payload,
  }
}
```
