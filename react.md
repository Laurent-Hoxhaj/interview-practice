# React Questions

From [this](https://dev.to/tylermcginnis/react-interview-questions) article.

**What is a High Order Component? Some use cases.**


**What happens when you call setState?**

The first thing React will do when setState is called is merge the object you passed into setState into the current state of the component.

This will kick off a process called reconciliation.

**What is the reconciliation process**

The end goal of reconciliation is to, in the most efficient way possible, update the UI based on this new state.

To do this, React will construct a new tree of React elements.

React will diff this new tree against the previous element tree.

By doing this, React will then know the exact changes which occurred, and by knowing exactly what changes occurred, will able to minimize its footprint on the UI by only making updates where absolutely necessary.

**What's the difference between an Element and a Component in React?**

Simply put, a React element describes what you want to see on the screen.

A React component is a function or a class which optionally accepts input and returns a React Element or another React Component (typically via JSX).

**What is JSX?**

[JSX Live Compiler](https://jsbin.com/hajabex/2/edit?output)

**When would you use a Class Component over a Functional Component?**

If your component has state or a lifecycle method(s), use a Class component. Otherwise, use a Functional component.

**What are refs in React?**

Refs are an escape hatch which allow you to get direct access to a DOM element or an instance of a component.

**What are keys in React and why are they important?**

Keys are what help React keep track of what items have changed, been added, or been removed from a list.

It's important that each key be unique among siblings.

**What is the difference between a controlled component and an uncontrolled component?**

A controlled component is a component where React is in control and is the single source of truth for the form data.

An uncontrolled component is where your form data is handled by the DOM, instead of inside your React component.

You use refs to accomplish this.

**Which is the suggested React Way? Why?**

It's typically recommended that you favor controlled components over uncontrolled components. The main reasons for this are that controlled components support instant field validation, allow you to conditionally disable/enable buttons, enforce input formats, and are more "the React way".

**In which lifecycle event do you make AJAX requests and why?**

AJAX requests should go in the componentDidMount lifecycle event.

**What does shouldComponentUpdate do and why is it important?**

What shouldComponentUpdate does is it's a lifecycle method that allows us to opt out of this reconciliation process for certain components.

**What is the second argument that can optionally be passed to setState and what is its purpose?**

A callback function which will be invoked when setState has finished and the component is re-rendered.

Something that's not spoken of a lot is that setState is asynchronous, which is why it takes in a second callback function. Typically it's best to use another lifecycle method rather than relying on this callback function, but it's good to know it exists.

**What is wrong with this code?**

```javascript
this.setState((prevState, props) => {
  return {
    streak: prevState.streak + props.count
  }
})
```

Nothing is wrong with it 🙂. It's rarely used and not well known, but you can also pass a function to setState that receives the previous state and props and returns a new state, just as we're doing above. And not only is nothing wrong with it, but it's also actively recommended if you're setting state based on previous state.
