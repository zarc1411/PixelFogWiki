---
sidebar_position: 1
---
# Fundamentals

## Create React App

Create React App is a comfortable environment for learning React, and is a best way to get started if you wanna build a SPA.

It sets up some boiler plate code

```bash
npx create-react-app my-app
cd my-app
npm start
```

## JSX

JSX is basically the syntax used to create React elements, it looks like HTML but isn't HTML

example

```jsx
const element = <h1>Hello, world!</h1>;
```

## Components

Components in React are nothing but functions. They can be reused, and basically denote a small part of an application.

In the example below, we have two components ``Welcome`` and ``App``, you can see in the render function that ``App`` component is rendered, into some element with an id ``root`` from the ``index.html`` page. The ``App`` component in turn composes ``Welcome`` component 3 times.

```jsx
const Welcome = (props) => {
  return <h1>Hello, {props.name}</h1>;
}

const App = () => {
  return (
    <div>
      <Welcome name="Sara" />
      <Welcome name="Cahal" />
      <Welcome name="Edite" />
    </div>
  );
}

ReactDOM.render(
  <App />,
  document.getElementById('root')
);
```

## Props

In the previous example, you can see props being passed as parameter in the ``Welcome`` component. That's what it is, a way to pass data to a component.

You can also destructure the props like this because props is just an object.

```jsx
const Welcome = ({name}) => {
  return <h1>Hello, {name}</h1>;
}
```

One thing you can't do with props though is that you can't change them directly.

So this is not allowed.

```jsx
const Welcome = (props) => {
  props.name = "Somethihng"; // Will throw an error
  return <h1>Hello, {props.name}</h1>;
}
```

But this is allowed
```jsx
const Welcome = (props) => {
  let name = props.name;
  name = "Somethihng" // Works
  return <h1>Hello, {name}</h1>;
}
```

But if you dynamically wanted to change the value you get from props, you wouldn't be able to do that. That's why state exists. We'll come to that later.

## Conditional rendering

In React, you can render a component based on some condition. So you render it only when the condition is met.

For example, here are two components

```jsx
const GreetUser = () => {
    return <h1>Hello user</h1>;
}

const GreetGuest = () => {
    return <h1>Hello guest</h1>;
}

const Greeter = ({isLoggedIn}) => {
    if(isLoggedIn){
        return <GreetUser/>
    }
    else{
        return <GreetGuest/>
    }
}

ReactDOM.render(
  // Try changing to isLoggedIn={true}:
  <Greeter isLoggedIn={false} />,
  document.getElementById('root')
);
```