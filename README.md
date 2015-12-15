# node-react-templates
 
Transparently `require()` .rt file from node with [react-templates](http://wix.github.io/react-templates) 
## Usage
 
`require('node-react-templates').install()` 

Then you can use .rt file in the react components for server side rendering.


## Example
The following is the example that using node-react-templates to render React components from node.

### React Templates Code --hello.rt
```
<div>
  <h3>Hello World</h3>
</div>
```
### React Components Code --hello.jsx
```
var React = require('react/addons');

var hellpTemplate = require("./hello.rt");

var Hello = React.createClass({
  
  render: function() {
    
    return hellpTemplate();
    
  }

});

module.exports = Hello;
```

### Server side rendering code --render.js
```
var React = require('react/addons');
require('node-jsx').install();
require('node-react-templates').install();

var compPath="./hello.jsx";

var component = require(compPath);
var contents = React.renderToString(React.createElement(component));

console.log(contents);

```
 

