---
title: React State Management with useReducer and useContext
date: "2023-03-23T21:20:30Z"
---
## Managing Ecommerce Cart State in a React Application Using useReducer and localStorage

In this blog post, we'll explore how to manage the state of an ecommerce cart in a React application without relying on external libraries. We'll use the `useReducer` hook for state management and `localStorage` for persistence. This approach will ensure that the cart state is persistent through reloads and across tabs or when navigating to different pages of the application.

## Overview

1. Introduction to `useReducer` and `localStorage`
2. Creating the cart context
3. Setting up the cart reducer
4. Creating actions for the cart
5. Implementing the cart provider
6. Accessing and updating the cart state in child components

## Introduction to `useReducer` and `localStorage`

The `useReducer` hook is part of the React library and provides a more organized way of managing complex state changes compared to `useState`. It works well with state objects that have multiple sub-values or when the next state depends on the previous one.

`localStorage` is a web storage API that allows developers to store key-value pairs in the browser. It provides a simple way to persist data across page refreshes and browser sessions.

## Creating the Cart Context

To make the cart state and dispatch function available to all components that need it, we'll create a cart context using `React.createContext` to share the cart state and dispatch function among our components. Create a `CartContext.js` file with the following content:
      
```js
// CartContext.js
import { createContext } from 'react';

export const CartContext = createContext();
```

## Setting Up the Cart Reducer and Actions for the Cart

The cart reducer is a function that takes the current state and an action as arguments and returns a new state based on the action type. We'll define the reducer function along with the initial state of the cart.

Actions are functions that dispatch an object containing the type of action and any relevant payload to the cart reducer. We'll define actions for adding items to the cart, removing items from the cart, and clearing the cart.

To create a reducer function that will handle our cart actions. In this example, we'll support the following actions: `'ADD_ITEM'`, `'REMOVE_ITEM'`, `'UPDATE_ITEM_QUANTITY'`, and `'CLEAR_CART'`. Create a `cartReducer.js` file with the following content:

```js
// cartReducer.js
export const cartReducer = (state, action) => {
  switch (action.type) {
    case 'ADD_ITEM':
      return [...state, action.item];
    case 'REMOVE_ITEM':
      return state.filter(item => item.id !== action.id);
    case 'UPDATE_ITEM_QUANTITY':
      return state.map(item =>
        item.id === action.id ? { ...item, quantity: action.quantity } : item
      );
    case 'CLEAR_CART':
      return [];
    default:
      return state;
  }
};
```
## Implementing the Cart Provider

To provide access to the cart state and dispatch function, we'll wrap the root component of our application with a cart provider component that takes care of initializing the cart state and providing it to all child components.


Provide the cart context to your child components by wrapping them with the CartContext.Provider component:

```js
return (
  <CartContext.Provider value={{ cart, dispatch }}>
    {/* Your child components here */}
  </CartContext.Provider>
);
```

## Accessing and Updating the Cart State in Child Components

Now that we have set up the cart context and provider, we can access the cart state and dispatch actions in our child components using the `useContext` hook. We'll show an example of how to add an item to the cart.


You can access the cart state and dispatch actions in your child components using the `useContext` hook. For example, here's how to add an item to the cart:

```js
import React, { useContext } from 'react';
import { CartContext } from './CartContext';

const Product = ({ product }) => {
  const { dispatch } = useContext(CartContext);

  const addToCart = () => {
    dispatch({
      type: 'ADD_ITEM',
      item: {
        id: product.id,
        name: product.name,
        price: product.price,
        quantity: 1,
      },
    });
  };

  return (
    <div>
      {/* Render product information */}
      <button onClick={addToCart}>Add to Cart</button>
    </div>
  );
}
```
## Conclusion

In this blog post, we explored how to manage the state of an ecommerce cart in a React application using the `useReducer` hook and `localStorage`. We also discussed how to set up a cart context, create a cart reducer, define actions for the cart, implement a cart provider, and access and update the cart state in child components. This approach provides a clean and organized way to manage complex state changes and ensure that the cart state persists across sessions and page refreshes.

