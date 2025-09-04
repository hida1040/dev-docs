# Snippets

This section describes JavaScript snippets that can be adopted in applications.

## Debounce

### Description
Debounce consolidates multiple consecutive operations (events) occurring within a specific interval into a single call.  
It is a technique used to control frequently triggered events, such as window resizing or key input,  
as well as unintended repeated executions of processes triggered by user actions.  

Debounce provides the following benefits:  
- **Performance improvement**  
  Suppresses unnecessary function execution, improving application performance.  
- **API cost reduction**  
  Reduces the number of API requests by suppressing unnecessary calls.  
- **Improved user experience**  
  Prevents unnecessary behavior or redundant animations and ensures effective user experience.  

Specifically, Debounce solves the following issues:  
- The same submit process was executed multiple times due to repeated user actions  
- APIs were called on every keystroke, causing performance concerns 

see: [MDN - Debounce](https://developer.mozilla.org/en-US/docs/Glossary/Debounce)

### function

```javascript
    /**
    * debounce()
    * Creates and returns a new debounced version of the given function.
    * This function delays execution until after the specified wait (ms) 
    * has elapsed since the last time it was invoked.
    * Useful for implementing behavior that should only occur 
    * once input has stopped arriving.
    * If the immediate argument is set to true, the function will be triggered 
    * at the start of the wait interval instead of the end.
    * This is helpful to prevent unintended double executions, 
    * such as when a "Submit" button is accidentally clicked twice.
    * @param {Function} func Function to debounce
    * @param {Number} wait Delay interval (milliseconds)
    * @param {Boolean} immediate Immediate trigger flag
    * @returns
    */
    function debounce(func, wait, immediate) {
        let timeout;
        return function() {
                const context = this, args = arguments;
                clearTimeout(timeout);
                timeout = setTimeout(function() {
                        timeout = null;
                        if (!immediate) func.apply(context, args);
                }, wait);
                if (immediate && !timeout) func.apply(context, args);
        };
    };
```

### Example Usage

This is an example of using Debounce for the **liveChange** event when typing into an Input field.  
Specify the function you want to apply as the first argument of `debounce()`.  
Set the delay time (in milliseconds) as the second argument of `debounce()`.  
In the example below, even if `onChangeInput` is called multiple times within 0.5 seconds,  
it will be consolidated into a single execution.  

```javaScript
    onChangeInput: debounce(function (oEvent) {
    ....
    }, 500),
```

