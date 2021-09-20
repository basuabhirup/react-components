# React Components and Styling:
## Objective of this Project:
* To undesrtand JSX and Babel
* To use Javascript Expressions in JSX
* To understand JSX attributes and inline styling 
* To create a React app from scratch that displays a dynamic greetings message, based on the time of the day _(it displays "Good Morning" if between midnight and 12PM, "Good Afternoon" if between 12PM and 6PM and "Good Night" if between 6PM and midnight)_
* To dynamically change the color of the greetings message, based on the time of the day _(Morning = red, Afternoon = green, Night = blue)_
* To split the main codebase into sevral components for modualrity and reusability

<div align="center">
  <img src="https://i.ibb.co/7rMZJXC/image.png" width=640px alt="Project Screentshot">
</div>

## Steps I have followed:
1. Installed `react` and `react-dom` dependencies and imported them inside the main `index.js` file:
```javascript
import React from "react";
import ReactDOM from "react-dom";
```
<br />

2. Created logic inside `index.js` file to get the browser's current time and accordingly change the value of two custom variables - `greeting` and `customStyle`:
```javascript
const date = new Date();
const currentTime = date.getHours();

let greeting;
const customStyle = {
  color: ""
};

if (currentTime < 12) {
  greeting = "Good Morning";
  customStyle.color = "red";
} else if (currentTime < 18) {
  greeting = "Good Afternoon";
  customStyle.color = "green";
} else {
  greeting = "Good Night";
  customStyle.color = "blue";
}
```
<br />

3. Rendered the JSX file containing these variables inside the parent div with id `root`:
```javascript
ReactDOM.render(
  <h1 className="heading" style={customStyle}>
    {greeting}
  </h1>,
  document.getElementById("root")
);
```
<br />

4. Finally splitted the main code in `index.js` into two components - `App` and `Heading` for reusability, modularity and a better readability:
```javascript
// Final Code inside 'index.js' file:
import React from "react";
import ReactDOM from "react-dom";
import App from "./components/App";

ReactDOM.render(<App />, document.getElementById("root"));
```

```javascript
// Final Code inside 'components/App.jsx' file:
import React from "react";
import Heading from "./Heading";

function App() {
  return (
    <div>
      <Heading />
    </div>
  );
}

export default App;
```

```javascript
// Final Code inside 'components/Heading.jsx' file:
import React from "react";

function Heading() {
  const date = new Date();
  const currentTime = date.getHours();

  let greeting;
  const customStyle = {
    color: ""
  };

  if (currentTime < 12) {
    greeting = "Good Morning";
    customStyle.color = "red";
  } else if (currentTime < 18) {
    greeting = "Good Afternoon";
    customStyle.color = "green";
  } else {
    greeting = "Good Night";
    customStyle.color = "blue";
  }

  return (
    <h1 className="heading" style={customStyle}>
      {greeting}
    </h1>
  );
}

export default Heading;
```
