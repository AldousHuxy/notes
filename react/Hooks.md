# React Hooks
 - Hooks are functions that let you "hook" into the React state and lifecycle features from function components.
## React Hook - useState
 - *useState* returns a state value and a function to update it.
 - RULES TO FOLLOW:
   - All state/lifecycle logic should be inside either a react, external, or custom hook.
   - All hooks should be declared at the top of the function.
   - Hooks cannot be conditional and must run in the same order they were declared.
```tsx
import { useState } from 'react';

const [value, setValue] = useState<string>('initial value')

function handleValueChange(newValue: string) {
    setValue(newValue)
    console.log(value)
}

return (
    <button onClick={() => handleValueChange('new value')}>Click Me!</button>
)
// new value
```
 - the update function additionally can take a callback to use the previous value.
 - the callback version MUST be used whenever the previous value is contingent for a calculation!
```tsx
import { useState } from 'react';

const [value, setValue] = useState<string>('initial value')

function handleValueChange() {
    setValue(prevValue => `${prev} updated`)
    console.log(value)
}

return (
    <button onClick={handleValueChange}>Click Me!</button>
)
// initial value updated
```
## React Hook - useEffect
 - *useEffect* performs side effect on functional components.
 - React components go through 4 lifecycle phases
    - Mount: component is added to the virtual DOM
    - Update: component is rerender with new state/props
    - Unmount: component is removed from the virtual DOM
    - Error Handling
 - Lifecycle methods are available in class components, but are increasingly unsupported.
```tsx
import { useEffect } from 'react';

useEffect(() => {
    console.log('component rerendered')
}, [])
// onMount: component rerendered
// onUpdate: component rerendered
// onUpdate: component rerendered
```
 - wrapping a fetch request in the useEffect hook prevents and infinite loop where the component rerenders causing the refetch causing a rerender.
```tsx
import { useEffect, useState } from 'react';

const [user, setUser] = useState<User|null>(null)

fetch('/api/users/auth')
    .then(res => res.json())
    .then(data => setUser(data))

return (
    <div>User: {!user ? 'loading...' : `${user.firstName} ${user.lastName}`}</div>
)
// User: loading...
// User: loading...
// User: loading...
```
 - the second parameter to useEffect is am array of values to render the component.
 - an empty array will only runs on component mount.
```tsx
import { useEffect, useState } from 'react';

const [user, setUser] = useState<User|null>(null)

useEffect(() => {
    fetch('/api/users/auth')
        .then(res => res.json())
        .then(data => setUser(data))
}, [])

return (
    <div>User: {!user ? 'loading...' : `${user.firstName} ${user.lastName}`}</div>
)
// User: loading...
// User: Miles Morales
```
 - passing a variable to the array will cause the component to render whenever the value changes.
```tsx
import { useEffect, useState } from 'react';

const [user, setUser] = useState<User|null>(null)
const [refetch, setRefetch] = useState<boolean>(false)

useEffect(() => {
    fetch('/api/users/auth')
        .then(res => res.json())
        .then(data => setUser(data))
}, [refetch])

return (
    <div>User: {!user ? 'loading...' : `${user.firstName} ${user.lastName}`}</div>
    <button onClick={() => setRefetch(!refetch)}>Refetch</button>
)
// User: loading...
// User: Miles Morales
// User: Miles Morales
// User: Miles Morales
```

## React Hook - useRef
```tsx
import { useRef, useState } from 'react';

const [email, setEmail] = useState('')
const emailRef = useRef()

const focus = () => {
    emailRef.current.focus()
}

return (
    <form>
        <input ref={emailRef} value={email} onChange={e => setEmail(e.target.value)} />
        <div>Your email: {email}</div>
        <button onClick={focus}>Focus</button>
    </form>
)
```

## React Hook - useId
 - `useId` returns a unique ID string associated with this particular useId call in this particular component.
```ts
import { useId } from 'react';

function PasswordField() {
  const passwordHintId = useId()
}
```

## React Hook - useMemo
 - Call `useMemo` at the top level of your component to cache a calculation between re-renders.
 - Basically, if the parameters of our function haven't changed then use the previously returned value rather than calculating the same value again.
```ts
export const doubleValue = (num: number) => {
    for (let i = 0; i < 1_000_000_000; i++) {}
    return num * 2
}
```
```tsx
import { useState } from 'react';

const [number, setNumber] = useState<number>(0)
const value = doubleValue(number)
```
```tsx
import { useCallback, useState } from 'react';

const [number, setNumber] = useState<number>(0)
const value = useMemo(() => {
    return doubleValue(number)
}, [number])
```

### Memoization
 - [Memoization](https://en.wikipedia.org/wiki/Memoization#:~:text=In%20computing%2C%20memoization%20or%20memoisation,the%20same%20inputs%20occur%20again.) is an optimization technique used primarily to speed up computer programs by storing the results of expensive function calls to pure functions and returning the cached result when the same inputs occur again.
 - It's derived from the latin word **memorandum** which means "to be remembered."

## React Hook - useCallback
 - `useCallback` is a React Hook that lets you cache a function definition between re-renders.
 - useMemo let's you memoize variables while useCallback let's you memoize function.
```tsx
const cachedFn = useCallback(fn, dependencies)
```


## React Hook - useReducer
 - **Parameters**:
   - *reducer*: The reducer function that specifies how the state gets updated. It must be pure, should take the state and action as arguments, and should return the next state. State and action can be of any types.
   - *initialArg*: The value from which the initial state is calculated. It can be a value of any type. How the initial state is calculated from it depends on the next init argument.
   - *init*(optional): The initializer function that should return the initial state. If it’s not specified, the initial state is set to initialArg. Otherwise, the initial state is set to the result of calling init(initialArg).
 - **Returns**:
   - The current state. During the first render, it’s set to init(initialArg) or initialArg (if there’s no init).
   - The dispatch function that lets you update the state to a different value and trigger a re-render.
```ts
import { useReducer } from 'react';

const reducer = (state, action) => {
    switch (action.type) {
        case 'increment':
            return { count: state.count + 1 }
        case 'decrement':
            return { count: state.count + 1 }
        default:
            return state
    }
}

export default function App() {
    const [state, dispatch] = useReducer(reducer, { count: 0 })

    const increment = () => {
        dispatch({ type: 'increment' })
    }

    const decrement = () => {
        dispatch({ type: 'decrement' })
    }

    return (
        <>
            <button onClick={decrement}>-</button>
            <span>{state.count}</span>
            <button onClick={increment}>+</button>
        </>
    )
} 
```

## React Hook - Context API
### Prop Drilling
 - Let's assume below that were fetching the data for the stateful value **name** in *Component A*, but we need access to that value in *Component I*.

![Prop Drilling](https://miro.medium.com/v2/resize:fit:982/1*4bxAkSA4oHcSAeAzzcJPHA.png)

### useContext/createContext
 - `useContext` call in a component is not affected by providers returned from the same component. The corresponding **<Context.Provider>** needs to be above the component doing the **useContext()** call.
 - `createContext` lets you create a context that components can provide or read.
```tsx
import { createContext } from 'react';
import { ComponentA } from './ComponentA';
import { ComponentB } from './ComponentB';

const NameContext = createContext()

const App = () => {
    const [name, setName] = useState<string>('')

    return (
        <NameContext.Provider value={name}>
            <ComponentA />
            <ComponentB />
        </NameContext.Provider>
    )
}

export default App;
```
```ts
import { useContext } from 'react';
import { NameContext } from './App';

const ComponentI = () => {
    const name = useContext(NameContext)
}
```
#### Context API Example
```tsx
import { createContext, useContext, useState } from 'react';
import { useLocalStorage } from '../hooks/useLocalStorage';

const ShoppingCartContext = createContext({})

export const useShoppingCart = () => {
    return useContext(ShoppingCartContext)
}

export const ShoppingCartProvider = ({ children }) => {
    const [isOpen, setIsOpen] = useState(false)
    const [cartItems, setCartItems] = useLocalStorage<CartItem[]>("CART",[])

    const openCart = () => setIsOpen(true)
    const closeCart = () => setIsOpen(false)

    const removeItemFromCart = (id: number) => {
        setCartItems(prev => {
            return prev.filter(item => item.id !== id)
        })
    }

    return (
        <ShoppingCartContext.Provider value={{
            openCart,
            closeCart,
            removeItemFromCart
        }}>
            {children}
            <ShoppingCart isOpen={isOpen} />
        </ShoppingCartContext.Provider>
    )
}

// somewhere else...
import { useShoppingCart } from './useShoppingCart';
import { ShoppingCartProvider } from './ShoppingCartContext';

export const ShopPage = () => {
    const { removeFromCart } = useShoppingCart()

    return (
        <ShoppingCartProvider>
            ...
        </ShoppingCartProvider>
    )
}
```

## React Hook - Custom Hooks
 - Custom hooks is way of creating non-native React hooks.
 - Hooks are just functions, the uniqueness comes with understanding React design patterns.
```ts
import { useEffect, useState } from 'react';

export function useLocalStorage<T>(key: string, initialValue: T | (() => T)) {
    const [value, setValue] = useState<T>(() => {
        const jsonValue = localStorage.getItem(key)
        if (jsonValue != null) return JSON.parse(jsonValue)

        if (typeof initialValue === "function") {
            return (initialValue as () => T)()
        } else {
            return initialValue
        }
    })

    useEffect(() => {
        localStorage.setItem(key, JSON.stringify(value))
    }, [key, value])

    return [value, setValue] as [typeof value, typeof setValue]
}
```