# satChooser.js
Allows you to add a little contextual popup area to a DIV or something on a page, and displays a grid of saturated colors for the user to choose from.  Returns a RGB color, with the idea that whatever color the user selected can then be programatically used to update some sort of theme or color choice.

It looks like this:

![](images/table satchooser.png?raw=true)

The 'sat' is for Saturation - the only colors displayed are fully saturated (in the HSL sense).  Any of these colors can then be tinted or shaded (lightened or darkened) depending on the needs of the UI.

# Example
You could put something like this in your head section:
```javascript

var sc;
function init(){
	sc = new satChooser({"clickCallback":setUserColorChoice});
	document.body.onclick = sc.hide();
}

```
Define a function to handle the callback:
```javascript

function setUserColorChoice(args){
	alert("Great, " + args.username + " chose " + args.colorstring);
}

````
The 'colorstring' and 'colorobject' properties of the passed argument will be set by whatever the user chose.

Then put something like this in the body:
```javascript

<button onclick='sc.show({"elem":this, "args":{"username":"joe"}});'>hi, joe! choose a color</button>

```
You can add additional arguments in the 'args' object that will be passed to your callback function.


## License
Copyright (C) 2014 Matthew LaGrandeur, released under [GPL 3.0](https://www.gnu.org/licenses/gpl-3.0-standalone.html)

## Author
| ![Matthew LaGrandeur's picture](https://1.gravatar.com/avatar/f6f7b963adc54db7e713d7bd5f4903ec?s=70) |
|---|
| [Matthew LaGrandeur](http://mattlag.com/) |
| matt[at]mattlag[dot]com |



