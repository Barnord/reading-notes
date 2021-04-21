# CSS
It makes things pretty. CSS is its own file that modified HTML to make it look different. You can also put them in your HTML doc with a ```<style></style>``` tag. Nesting matters for CSS docs, as there are sibling selectors.

## Doubling Down
If two rules apply to the same element, the second one takes precedence, unless one is marked with an exclamation, ! marks a rule as important, so it will take precedence. More specific rules also take precedence.

## Color
Color can be expressed in three ways, you can name the color, you can input the hex code, or you can put in the rgb value.
```
h1 {
    color: DarkCyan;
}

h2 {color: #ee3e80
}

p {color: rgb(100,100,90);
}
```
 ## Opacity
 You can mark opacity on a scale of 0-1
 ```
 p {background-color: rgb(0,0,0);
 opacity: 0.5;}

p {background-color: rgba(0,0,0,0.5);
    background-color: rgb(0,0,0)
}
```
Older browsers don't support opacity, so it's important to leave a fallback when using rgba.

## HSL
You can also change the Hue, Saturation, and Lightness of a color with HSL. Hue is displayed as a number between 0-360, as it's an angle. Saturation is a percentage. Lightness is also a percentage, with 0% being white, and 100% being black. You can also use the HSLA tag to add a transparancy value to the end, which, like rgba, is represented by a value between 0-1.




[<==Back](README.md)
