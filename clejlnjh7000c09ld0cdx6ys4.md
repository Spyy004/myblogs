# What Why How: MobX. (A state management solution)

## Introduction

Welcome back to the WhatWhyHow series, in the last article, we covered the WhatWhyHow of Flutter, this week, we are going to look into the WhatWhyHow of Mobx.

MobX is a state management library for JavaScript applications. It is commonly used with React, but it can also be used with other frameworks or libraries. MobX simplifies the process of managing the state in your application by providing a simple, reactive way to update and access data. In this blog post, we will discuss what MobX is, why you should consider using it, and how to get started.

## What is MobX?

MobX is a state management library that provides a simple and efficient way to manage the state in your application. It is based on the principles of reactive programming and uses Observables to track state changes. This means that whenever a change is made to your data, MobX automatically updates any components or views that depend on that data.

MobX provides three main building blocks:

1. Observables: These are objects or values that can be observed for changes. Whenever an observable changes, MobX automatically updates any component or view that depends on it.
    
2. Actions: These are functions that modify observables. Whenever an action is executed, MobX tracks the changes it makes to observables and updates any components or views that depend on them.
    
3. Reactions: These are functions that depend on observables and are automatically re-run whenever an observable changes. Reactions can be used to update the component state, trigger side effects, or perform other tasks.
    

## Why use MobX?

There are several reasons why you might want to consider using MobX in your application:

1. Simple and intuitive API: MobX provides a simple and intuitive API that is easy to understand and use. This makes it a great choice for developers of all skill levels.
    
2. Efficient updates: MobX uses reactive programming principles to track state changes and only updates the parts of your application that need to be updated. This makes it much more efficient than other state management libraries.
    
3. Flexibility: MobX can be used with any framework or library, not just React. This means that you can use it in any JavaScript application, regardless of what tools you are using.
    
4. Scalability: MobX provides a scalable way to manage the state of your application. As your application grows and becomes more complex, MobX can help you manage the state in a way that is maintainable and easy to understand.
    

## How to use MobX?

Using MobX in your application is relatively straightforward. Here are the basic steps:

1. Install MobX and MobX React:
    

`npm install mobx mobx-react`

1. Create an observable:
    

```javascript
import { observable } from "mobx";

const todoList = observable({
  todos: [],
});
```

1. Create an action:
    

```javascript
import { action } from "mobx";

const addTodo = action((todo) => {
  todoList.todos.push(todo);
});
```

1. Use the observable and action in your components
    

```javascript
import { observer } from "mobx-react";

const TodoList = observer(() => {
  return (
    <ul>
      {todoList.todos.map((todo) => (
        <li>{todo}</li>
      ))}
    </ul>
  );
});

const AddTodo = observer(() => {
  const [inputValue, setInputValue] = useState("");

  const handleSubmit = (e) => {
    e.preventDefault();
    addTodo(inputValue);
    setInputValue("");
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        type="text"
        value={inputValue}
        onChange={(e) => setInputValue(e.target.value)}
      />
      <button type="submit">Add Todo</button>
    </form>
  );
});
```

In this example, we create an observable object called `todoList` that contains an array of todos. We also create an action called `addTodo` that takes a todo as an argument and adds it to the `todos` array.

We then use the `observer` function from `mobx-react` to create two React components: `TodoList` and `AddTodo`. The `TodoList` component renders the list of todos from the `todoList` observable, and the `AddTodo` component allows the user to add a new todo by calling the `addTodo` action.

Note that we use the `observer` function to create our components. This function makes our components reactive to changes in observables, meaning that any changes to the `todoList` observable will automatically trigger a re-render of the `TodoList` component.

## How does Mobx work?

Under the hood, MobX uses a technique called "observables" to track changes in state. Observables are special JavaScript objects that can be observed for changes. They work like a magic mirror that reflects changes made to them. When an observable changes, MobX automatically updates any components or views that depend on it.

So, if you have a component that relies on an observable value, and that value changes, MobX will automatically update the component to reflect the new value. This makes it easy to manage the state of your application without having to manually update your views or components.

To create an observable in MobX, you simply wrap your value in a function or a decorator. This tells MobX to track changes to that value and notify any observers when the value changes.

When you modify an observable, MobX creates a new "action" to record the changes made to the observable. An action is simply a function that modifies observables. Actions are executed in a batched manner to optimize performance. This means that if you make multiple changes to observables within an action, MobX will batch those changes together and only update any dependent components once, after the action has finished executing.

MobX also uses "reactions" to automatically update components or views that depend on observables. Reactions are functions that are executed whenever an observable changes and they can be used to update the component state, trigger side effects, or perform other tasks. You can think of reactions as the "watchers" in Vue.js or the "useEffect" hook in React.

By using observables, actions, and reactions, MobX provides a simple and efficient way to manage the state in your application. With MobX, you can create reactive and scalable applications that are easy to understand and update.

## Conclusion

In conclusion, MobX is a powerful and flexible state management library for JavaScript applications. It provides a simple and intuitive API that makes managing the state easy and efficient. With MobX, you can create scalable and maintainable applications that are easy to understand and update. If you are looking for a state management library for your JavaScript application, consider giving MobX a try.

I hope you learned something new today. For more such informative blogs on tech. Follow CompSciWithIyush.