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


#### References

https://egghead.io/lessons/react-create-html-elements-with-react-s-createelement-api
https://reactjs.org/blog/2015/12/18/react-components-elements-and-instances.html
https://www.taniarascia.com/getting-started-with-react/
