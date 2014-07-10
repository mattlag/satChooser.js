# satChooser.js
Allows you to add a little contextual popup area to a DIV or something on a page, and displays a grid of saturated colors for the user to choose from.  Returns a RGB color, with the idea that whatever color the user selected can then be programatically used to update some sort of theme or color choice.

It looks like this:
![](images/table 'data:image/png;base64,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wQV/uuSDC9604EULvmlKLRG1SXbYDiMCMwpZKWSlkJVCVg5ZKWSlkJVCVgpZjRDMKGSlkJVCVgpZjQjMKGSlkJVCVgpZOWSlkJVCVgpZOWZnaomoTbLDdhgRmFHISiErhawUsnLISiErhawUslLIaoRgRiErhawUslLIakRgRiErhawUslLIyiErhawUslLIyjE7U0tEbZIdtsOIwIxCVgpZKWSlkJVDVgpZKWSlkJVCViMEMwpZKWSlkJVCViMCMwpZKWSlkJVCVg5ZKWSlkJVCVo7ZmVoiapPssB1GBGYUslLISiErhawcslLISiErhawUshohmFHISiErhawUshoRmFHISiErhawUsnLISiErhawUsnLMztQSUZtkh+0wIjCjkJVCVgpZKWTlkJVCVgpZKWSlkNUIwYxCVgpZKWSlkNWIwIxCVgpZKWSlkJVDVgpZKWSlkJVjdqaWiNokO2yHEYEZhawUslLISiErh6wUslLISiErhaxGCGYUslLISiErhaxGBGYUslLISiErhawcslLISiErhawcszO1RNQm2WE7jAjMKGSlkJVCVgpZOWSlkJVCVgpZKWQ1QjCjkJVCVgpZKWQ1IjCjkJVCVgpZKWTlkJVCVgpZKWTlmJ2pJaI2yQ7bYURgRiErhawUslLIyiErhawUslLISiGrEYIZhawUslLISiGrEYEZhawUslLISiErh6wUslLISiErx+xMLRG1Sa572P7ky7987lsW3LrgjQvev+BP5t6/4I0Lbl3wLQu+fMm3LLh1wRsXvH/Bn8y9f8EbF9y64FsWfPnctyy4dcEbF7x/wZ8sef+CNy64dcG3TKklojbJDtthRGBGISuFrBSyUsjKISuFrBSyUshKIasRghmFrBSyUshKIasRgRmFrBSyUshKISuHrBSyUshKISvH7EwtEbVJdtgOIwIzClkpZKWQlUJWDlkpZKWQlUJWClmNEMwoZKWQlUJWClmNCMwoZKWQlUJWClk5ZKWQlUJWClk5ZmdqiahNssN2GBGYUchKISuFrBSycshKISuFrBSyUshqhGBGISuFrBSyUshqRGBGISuFrBSyUsjKISuFrBSyUsjKMTtTS0Rtkh22w4jAjEJWClkpZKWQlUNWClkpZKWQlUJWIwQzClkpZKWQlUJWIwIzClkpZKWQlUJWDlkpZKWQlUJWjtmZWiJqk+ywHUYEZhSyUshKISuFrByyUshKISuFrBSyGiGYUchKISuFrBSyGhGYUchKISuFrBSycshKISuFrBSycszO1BJRm2SH7TAiMKOQlUJWClkpZOWQlUJWClkpZKWQ1QjBjEJWClkpZKWQ1YjAjEJWClkpZKWQlUNWClkpZKWQlWN2ppaI2iQ7bIcRgRmFrBSyUshKISuHrBSyUshKISuFrEYIZhSyUshKISuFrEYEZhSyUshKISuFrByyUshKISuFrByzM7VE1CbZYTuMCMwoZKWQlUJWClk5ZKWQlUJWClkpZDVCMKOQlUJWClkpZDUiMKOQlUJWClkpZOWQlUJWClkpZOWYnaklojbJdQ/bQ1/xFXNPX3DrgjcseN+Ch+bet+ANC25d8PQFX7Hk6QtuXfCGBe9b8NDc+xa8YcGtC56+4Cvmnr7g1gVvWPC+BQ8ted+CNyy4dcHTp9QSUZtkh+0wIjCjkJVCVgpZKWTlkJVCVgpZKWSlkNUIwYxCVgpZKWSlkNWIwIxCVgpZKWSlkJVDVgpZKWSlkJVjdqaWiNokO2yHEYEZhawUslLISiErh6wUslLISiErhaxGCGYUslLISiErhaxGBGYUslLISiErhawcslLISiErhawcszO1RNQm2WE7jAjMKGSlkJVCVgpZOWSlkJVCVgpZKWQ1QjCjkJVCVgpZKWQ1IjCjkJVCVgpZKWTlkJVCVgpZKWTlmJ2pJaI2yQ7bYURgRiErhawUslLIyiErhawUslLISiGrEYIZhawUslLISiGrEYEZhawUslLISiErh6wUslLISiErx+xMLRG1SXbYDiMCMwpZKWSlkJVCVg5ZKWSlkJVCVgpZjRDMKGSlkJVCVgpZjQjMKGSlkJVCVgpZOWSlkJVCVgpZOWZnaomoTbLDdhgRmFHISiErhawUsnLISiErhawUslLIaoRgRiErhawUslLIakRgRiErhawUslLIyiErhawUslLIyjE7U0tEbZIdtsOIwIxCVgpZKWSlkJVDVgpZKWSlkJVCViMEMwpZKWSlkJVCViMCMwpZKWSlkJVCVg5ZKWSlkJVCVo7ZmVoiapPssB1GBGYUslLISiErhawcslLISiErhawUshohmFHISiErhawUshoRmFHISiErhawUsnLISiErhawUsnLMztQSUZvkuoftY1/5lXPPXPB9C16/4BcWfGzuFxa8fsH3LXjmgq9c8swF37fg9Qt+YcHH5n5hwesXfN+CZy74yrlnLvi+Ba9f8AsLPrbkFxa8fsH3LXjmlFoiapPssB1GBGYUslLISiErhawcslLISiErhawUshohmFHISiErhawUshoRmFHISiErhawUsnLISiErhawUsnLMztQSUZtkh+0wIjCjkJVCVgpZKWTlkJVCVgpZKWSlkNUIwYxCVgpZKWSlkNWIwIxCVgpZKWSlkJVDVgpZKWSlkJVjdqaWiNokO2yHEYEZhawUslLISiErh6wUslLISiErhaxGCGYUslLISiErhaxGBGYUslLISiErhawcslLISiErhawcszO1RNQm2WE7jAjMKGSlkJVCVgpZOWSlkJVCVgpZKWQ1QjCjkJVCVgpZKWQ1IjCjkJVCVgpZKWTlkJVCVgpZKWTlmJ2pJaI2yQ7bYURgRiErhawUslLIyiErhawUslLISiGrEYIZhawUslLISiGrEYEZhawUslLISiErh6wUslLISiErx+xMLRG1SXbYDiMCMwpZKWSlkJVCVg5ZKWSlkJVCVgpZjRDMKGSlkJVCVgpZjQjMKGSlkJVCVgpZOWSlkJVCVgpZOWZnaomoTbLDdhgRmFHISiErhawUsnLISiErhawUslLIaoRgRiErhawUslLIakRgRiErhawUslLIyiErhawUslLIyjE7U0tEbZIdtsOIwIxCVgpZKWSlkJVDVgpZKWSlkJVCViMEMwpZKWSlkJVCViMCMwpZKWSlkJVCVg5ZKWSlkJVCVo7ZmVoiapNc97B99Ku+au6WBS9e8PoFP7fgo3M/t+D1C1684JYFX7XklgUvXvD6BT+34KNzP7fg9QtevOCWBV81d8uCFy94/YKfW/DRJT+34PULXrzglim1RNQm2WE7jAjMKGSlkJVCVgpZOWSlkJVCVgpZKWQ1QjCjkJVCVgpZKWQ1IjCjkJVCVgpZKWTlkJVCVgpZKWTlmJ2pJaI2yQ7bYURgRiErhawUslLIyiErhawUslLISiGrEYIZhawUslLISiGrEYEZhawUslLISiErh6wUslLISiErx+xMLRG1SXbYDiMCMwpZKWSlkJVCVg5ZKWSlkJVCVgpZjRDMKGSlkJVCVgpZjQjMKGSlkJVCVgpZOWSlkJVCVgpZOWZnaomoTbLDdhgRmFHISiErhawUsnLISiErhawUslLIaoRgRiErhawUslLIakRgRiErhawUslLIyiErhawUslLIyjE7U0tEbZIdtsOIwIxCVgpZKWSlkJVDVgpZKWSlkJVCViMEMwpZKWSlkJVCViMCMwpZKWSlkJVCVg5ZKWSlkJVCVo7ZmVoiapPssB1GBGYUslLISiErhawcslLISiErhawUshohmFHISiErhawUshoRmFHISiErhawUsnLISiErhawUsnLMztQSUZtkh+0wIjCjkJVCVgpZKWTlkJVCVgpZKWSlkNUIwYxCVgpZKWSlkNWIwIxCVgpZKWSlkJVDVgpZKWSlkJVjdqaWiNokO2yHEYEZhawUslLISiErh6wUslLISiErhaxGCGYUslLISiErhaxGBGYUslLISiErhawcslLISiErhawcszO1RNQmue5h++2v+Zq5b13w/Qtet+BnF/z23M8ueN2C71/wrQu+Zsm3Lvj+Ba9b8LMLfnvuZxe8bsH3L/jWBV8z960Lvn/B6xb87ILfXvKzC1634PsXfOuUWiJqk+ywHUYEZhSyUshKISuFrByyUshKISuFrBSyGiGYUchKISuFrBSyGhGYUchKISuFrBSycshKISuFrBSycszO1BJRm2SH7TAiMKOQlUJWClkpZOWQlUJWClkpZKWQ1QjBjEJWClkpZKWQ1YjAjEJWClkpZKWQlUNWClkpZKWQlWN2ppaI2iQ7bIcRgRmFrBSyUshKISuHrBSyUshKISuFrEYIZhSyUshKISuFrEYEZhSyUshKISuFrByyUshKISuFrByzM7VE1CbZYTuMCMwoZKWQlUJWClk5ZKWQlUJWClkpZDVCMKOQlUJWClkpZDUiMKOQlUJWClkpZOWQlUJWClkpZOWYnaklojbJDtthRGBGISuFrBSyUsjKISuFrBSyUshKIasRghmFrBSyUshKIasRgRmFrBSyUshKISuHrBSyUshKISvH7EwtEbVJdtgOIwIzClkpZKWQlUJWDlkpZKWQlUJWClmNEMwoZKWQlUJWClmNCMwoZKWQlUJWClk5ZKWQlUJWClk5ZmdqiahNssN2GBGYUchKISuFrBSycshKISuFrBSyUshqhGBGISuFrBSyUshqRGBGISuFrBSyUsjKISuFrBSyUsjKMTtTS0Rtkh22w4jAjEJWClkpZKWQlUNWClkpZKWQlUJWIwQzClkp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rBSyUshKISuHrBSyUshKISvH7EwtEbVJdtgOIwIzClkpZKWQlUJWDlkpZKWQlUJWClmNEMwoZKWQlUJWClmNCMwoZKWQlUJWClk5ZKWQlUJWClk5ZmdqiahNct3D9oFv/ua571rwAwt+bMG7F3xg7t0LfmzBDyz4rgXfvOS7FvzAgh9b8O4FH5h794IfW/ADC75rwTfPfdeCH1jwYwveveADS9694McW/MCC75pSS0Rtkh22w4jAjEJWClkpZKWQlUNWClkpZKWQlUJWIwQzClkpZKWQlUJWIwIzClkpZKWQlUJWDlkpZKWQlUJWjtmZWiJqk+ywHUYEZhSyUshKISuFrByyUshKISuFrBSyGiGYUchKISuFrBSyGhGYUchKISuFrBSycshKISuFrBSycszO1BJRm2SH7TAiMKOQlUJWClkpZOWQlUJWClkpZKWQ1QjBjEJWClkpZKWQ1YjAjEJWClkpZKWQlUNWClkpZKWQlWN2ppaI2iQ7bIcRgRmFrBSyUshKISuHrBSyUshKISuFrEYIZhSyUshKISuFrEYEZhSyUshKISuFrByyUshKISuFrByzM7VE1CbZYTuMCMwoZKWQlUJWClk5ZKWQlUJWClkpZDVCMKOQlUJWClkpZDUiMKOQlUJWClkpZOWQlUJWClkpZOWYnaklojbJDtthRGBGISuFrBSyUsjKISuFrBSyUshKIasRghmFrBSyUshKIasRgRmFrBSyUshKISuHrBSyUshKISvH7EwtEbVJdtgOIwIzClkpZKWQlUJWDlkpZKWQlUJWClmNEMwoZKWQlUJWClmNCMwoZKWQlUJWClk5ZKWQlUJWClk5ZmdqiahNssN2GBGYUchKISuFrBSycshKISuFrBSyUshqhGBGISuFrBSyUshqRGBGISuFrBSyUsjKISuFrBSyUsjKMTtTS0Rtkusetvc9/elzz1nw0gX3LnjXgvfNvWvBvQteuuA5C56+5DkLXrrg3gXvWvC+uXctuHfBSxc8Z8HT556z4KUL7l3wrgXvW/KuBfcueOmC50ypJaI2yQ7bYURgRiErhawUslLIyiErhawUslLISiGrEYIZhawUslLISiGrEYEZhawUslLISiErh6wUslLISiErx+xMLRG1SXbYDiMCMwpZKWSlkJVCVg5ZKWSlkJVCVgpZjRDMKGSlkJVCVgpZjQjMKGSlkJVCVgpZOWSlkJVCVgpZOWZnaomoTbLDdhgRmFHISiErhawUsnLISiErhawUslLIaoRgRiErhawUslLIakRgRiErhawUslLIyiErhawUslLIyjE7U0tEbZIdtsOIwIxCVgpZKWSlkJVDVgpZKWSlkJVCViMEMwpZKWSlkJVCViMCMwpZKWSlkJVCVg5ZKWSlkJVCVo7ZmVoiapPssB1GBGYUslLISiErhawcslLISiErhawUshohmFHISiErhawUshoRmFHISiErhawUsnLISiErhawUsnLMztQSUZtkh+0wIjCjkJVCVgpZKWTlkJVCVgpZKWSlkNUIwYxCVgpZKWSlkNWIwIxCVgpZKWSlkJVDVgpZKWSlkJVjdqaWiNokO2yHEYEZhawUslLISiErh6wUslLISiErhaxGCGYUslLISiErhaxGBGYUslLISiErhawcslLISiErhawcszO1RNQm2WE7jAjMKGSlkJVCVgpZOWSlkJVCVgpZKWQ1QjCjkJVCVgpZKWQ1IjCjkJVCVgpZKWTlkJVCVgpZKWTlmJ2pJaI2yXUP288/61lz373gBxfcu+DtC35+7u0L7l3wgwu+e8Gzlnz3gh9ccO+Cty/4+bm3L7h3wQ8u+O4Fz5r77gU/uODeBW9f8PNL3r7g3gU/uOC7p9QSUZtkh+0wIjCjkJVCVgpZKWTlkJVCVgpZKWSlkNUIwYxCVgpZKWSlkNWIwIxCVgpZKWSlkJVDVgpZKWSlkJVjdqaWiNokO2yHEYEZhawUslLISiErh6wUslLISiErhaxGCGYUslLISiErhaxGBGYUslLISiErhawcslLISiErhawcszO1RNQm2WE7jAjMKGSlkJVCVgpZOWSlkJVCVgpZKWQ1QjCjkJVCVgpZKWQ1IjCjkJVCVgpZKWTlkJVCVgpZKWTlmJ2pJaI2yQ7bYURgRiErhawUslLIyiErhawUslLISiGrEYIZhawUslLISiGrEYEZhawUslLISiErh6wUslLISiErx+xMLRG1SXbYDiMCMwpZKWSlkJVCVg5ZKWSlkJVCVgpZjRDMKGSlkJVCVgpZjQjMKGSlkJVCVgpZOWSlkJVCVgpZOWZnaomoTbLDdhgRmFHISiErhawUsnLISiErhawUslLIaoRgRiErhawUslLIakRgRiErhawUslLIyiErhawUslLI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VgpZjQjMKGSlkJVCVgpZOWSlkJVCVgpZOWZnaomoTbLDdhgRmFHISiErhawUsnLISiErhawUslLIaoRgRiErhawUslLIakRgRiErhawUslLIyiErhawUslLIyjE7U0tEbZIdtsOIwIxCVgpZKWSlkJVDVgpZKWSlkJVCViMEMwpZKWSlkJVCViMCMwpZKWSlkJVCVg5ZKWSlkJVCVo7ZmVoiapPssB1GBGYUslLISiErhawcslLISiErhawUshohmFHISiErhawUshoRmFHISiErhawUsnLISiErhawUsnLMztQSUZvkuoftDbfeOvfSBXctuGfBvQveMHfvgnsW3LXgpQtuXfLSBXctuGfBvQveMHfvgnsW3LXgpQtunXvpgrsW3LPg3gVvWHLvgnsW3LXgpVNqiahNssN2GBGYUchKISuFrBSycshKISuFrBSyUshqhGBGISuFrBSyUshqRGBGISuFrBSyUsjKISuFrBSyUsjKMTtTS0Rtkh22w4jAjEJWClkpZKWQlUNWClkpZKWQlUJWIwQzClkpZKWQlUJWIwIzClkpZKWQlUJWDlkpZKWQlUJWjtmZWiJqk+ywHUYEZhSyUshKISuFrByyUshKISuFrBSyGiGYUchKISuFrBSyGhGYUchKISuFrBSycshKISuFrBSycszO1BJRm2SH7TAiMKOQlUJWClkpZOWQlUJWClkpZKWQ1QjBjEJWClkpZKWQ1YjAjEJWClkpZKWQlUNWClkpZKWQlWN2ppaI2iQ7bIcRgRmFrBSyUshKISuHrBSyUshKISuFrEYIZhSyUshKISuFrEYEZhSyUshKISuFrByyUshKISuFrByzM7VE1CbZYTuMCMwoZKWQlUJWClk5ZKWQlUJWClkpZDVCMKOQlUJWClkpZDUiMKOQlUJWClkpZOWQlUJWClkpZOWYnaklojbJDtthRGBGISuFrBSyUsjKISuFrBSyUshKIasRghmFrBSyUshKIasRgRmFrBSyUshKISuHrBSyUshKISvH7EwtEbVJdtgOIwIzClkpZKWQlUJWDlkpZKWQlUJWClmNEMwoZKWQlUJWClmNCMwoZKWQlUJWClk5ZKWQlUJWClk5ZmdqiahNct3Ddt9tt83dvuDuBfcseM2C++Zes+CeBXcvuH3BbUtuX3D3gnsWvGbBfXOvWXDPgrsX3L7gtrnb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'?raw=true)

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



