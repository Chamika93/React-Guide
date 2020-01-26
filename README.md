# React-Guide

## Components and Elements

In react components are made from React.Createlement API and jsx is syntactical sugar to make it easier to understand.First let's create a very simple react element and compare this with a javascript element.

First let's create a simple div element in vanila javascrtipt from the below code.

```
 <script>
      const rootElement = document.getElementById("root");
      const element = document.createElement("div");
      element.textContent = "test";
      element.className = "container";
      rootElement.appendChild(element);
 </script>
```

Equivalent react code goes as follows.

```
<script>
     const rrootElement = document.getElementById("rootReact");
   const relement = React.createElement("div", {
        className: "container",
        children: "React test"
      });
     ReactDOM.render(relement, rrootElement);
 </script>

```
As you can see createElement take 2 arguments 
    1. type of the element
    2. propearties object of the element ( this goes as the props in react )
    
So If we want to create a nested element we can pass the inner element to the children field as follows.

```
<script>
      const rrootElement = document.getElementById("rootReact");
      const test = React.createElement("div", {
        children: React.createElement("p", null, "Hello world")
      });

      ReactDOM.render(test, rrootElement);
 </script>
````
This creates a simple `<div><p>Hello World</p></div>` element in the dom. Let's try to undersatand how this works and create a reusable component.

**React.createElement** takes 2 inputs first input is the type of the element if it is a known DOM element like div,p or h1 it is passed as a string like "div","p" or "h1". Or type can be a function or a class. Second input is the element properties object and this is going to pass in to the function or class to create the element tree.

```
<script>
    function Div(props) {
        return React.createElement("div", props);
    }
    const rrootElement = document.getElementById("rootReact");
    const test = React.createElement(Div, {
        children: React.createElement("p", null, "Hello world")
     });
     ReactDOM.render(test, rrootElement);
</script>

```
In the above code function Div is passed to the createElement method and properties object get passed in to the function as a parameter. So the above code is equivalent to following code.

```
const test = React.createElement("div", {
        children: React.createElement("p", null, "Hello world")
      });
```
So React.createElement will call the same funtion in a nested way until it creates an elment tree from known elements. As you can see data flows from parent to child inside the props object. We can pass functions and variables inside the props object.Even though we can create a react app completely from React.createElement method calls there is a better way to do this which is called **JSX** which is very similar to html syntax and it will simplify the component creating process for us.

#### Guide

1. JSX element can be write in 2 different ways

`<div>Helloworld</div>` or `<div children="Helloworld" />`

So content between opening and closing tags will be added to children attribute in props object. Or in the self enclosing way you can directly specify that. 

2. If you want anyother variable or function needs to pass through props object you can directly specify that in the opening tag or in the self enclosing tag.

`<div className="hello" test="test">Helloworld</div>`
So the props object get pass to the createElement look like this.
```
props = {
 children:"Helloworld",
 className:"hello",
 test:"hello"
}

```
3. Ceate a custom component - In createElement type can be a string or funcion/class . In order to JSX to identify this if  tag  start from a simple letter it will pass the type as a string to createElement menthod and if it starts from a capital letter JSX will pass the value as a function/class

#### References

https://egghead.io/lessons/react-create-html-elements-with-react-s-createelement-api
https://reactjs.org/blog/2015/12/18/react-components-elements-and-instances.html
https://www.taniarascia.com/getting-started-with-react/
https://www.academind.com/learn/react/redux-vs-context-api/
https://daveceddia.com/what-is-a-thunk/
https://reactjs.org/docs/context.html
