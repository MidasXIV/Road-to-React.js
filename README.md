<p align="center">
  <h1 align="center">Learning React</h1>
</p>


<p align="center">
  <a href="#introduction">Introduction</a>
</p>

***

# Introduction
* Faster than applications developed in vanilla javascript.
	* -> Because of virtualDom.
* Reusable Web Components.
	* -> Cleaner Code.
* Maintained by Facebook.
* Very in demand Framework for front end development.

1. `Components` : 
	* JSX : javascript wrapper.
	* Props : State.
	* Must Know HTML, CSS, JS, ES6 (2015).
	
```javascript
import React from "react"
import ReactDOM from "react-dom"

ReactDOM.render(What do i want to render, where do i want to render it)
//JSX : javascript rendering HTML
ReactDOM.render(<h1>React Introduction</h1>, document.getElementById("root"))

```

### My first Component

```javascript
import React from "react"
function MyInfo() {
	return (
		<div>
			<h1>Heading</h1>
			<p>Paragraph</p>
			<ul>
				<li>aaa</li>
				<li>bbb</li>
				<li>ccc</li>
			</ul>
		</div>
	)
}
```
