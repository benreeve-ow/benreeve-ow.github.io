---
layout: post
title:  "Experimenting with React Custom Hooks"
date:   2023-01-05 16:45:00 -0500
categories: [experiments]
author: Your Name
---

I've been working on improving my React skills by creating custom hooks. React's hooks API provides a great way to extract and reuse stateful logic between components.

## What Are Custom Hooks?

Custom hooks are JavaScript functions that start with "use" and may call other hooks. They let you extract component logic into reusable functions.

## My useLocalStorage Hook

Here's a custom hook I created to simplify working with localStorage:

```jsx
import { useState, useEffect } from 'react';

function useLocalStorage(key, initialValue) {
  // Get stored value or use initial value
  const [storedValue, setStoredValue] = useState(() => {
    try {
      const item = window.localStorage.getItem(key);
      return item ? JSON.parse(item) : initialValue;
    } catch (error) {
      console.error(error);
      return initialValue;
    }
  });

  // Update localStorage when state changes
  useEffect(() => {
    try {
      window.localStorage.setItem(key, JSON.stringify(storedValue));
    } catch (error) {
      console.error(error);
    }
  }, [key, storedValue]);

  return [storedValue, setStoredValue];
}
```

## Using the Hook

Here's how you can use this hook in a component:

```jsx
function MyComponent() {
  const [name, setName] = useLocalStorage('name', '');
  
  return (
    <div>
      <input
        type="text"
        value={name}
        onChange={e => setName(e.target.value)}
        placeholder="Enter your name"
      />
      <p>Hello, {name || 'stranger'}!</p>
    </div>
  );
}
```

## Benefits I've Found

- Cleaner component code
- Reusable stateful logic
- Better separation of concerns
- Easier testing

I'll continue experimenting with custom hooks and share more findings in future posts! 