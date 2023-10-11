
# theme.js

Easy theme switcher for websites written in Javascript. Remebers previous user selected themes upon loading and sets a random theme upon first page load. Support for any number of themes and keyboard shortcut integration.


## Usage/Examples
Add the following code to your project files or add them as seperate files in the project directory.

*.js and *.css respectively and replace (theme1,theme2) with suitable names.
### JS
```javascript
const toggleThemeBtn = document.querySelector('[data-theme-btn]');
// add the data-theme-btn property to your theme button in HTML
const themes = [' theme1 ',' theme2 '];
// intilialize array with themes
const storedTheme = localStorage.getItem('theme') || (localStorage.setItem('theme', themes[0]), themes[0]);
// fetch previously stored theme from local storage and set a new theme if local storage is empty i.e. first page load

function setTheme(theme) {
  document.documentElement.setAttribute('data-theme', theme);
  localStorage.setItem('theme', theme);
}
// function to set theme and assign theme to local storage to store user preference
function setThemeCycle() {
  const currentTheme = document.documentElement.getAttribute('data-theme');
  setTheme(themes[(themes.indexOf(currentTheme) + 1) % themes.length]);
}
// function to cycle through themes in order when user presses the theme button

document.addEventListener('DOMContentLoaded', () => setTheme(storedTheme));
// sets theme upon page load and also waits until DOM content is loaded
toggleThemeBtn.addEventListener('click', setThemeCycle);
// checks if theme button is clicked and cycles through selected themes
document.addEventListener('keydown', event => {
    if (event.code === ' add key here ') {
      setThemeCycle();
      event.preventDefault();
    }
});
// keybind to cycle through themes
// keycodes for corresponding keys can be found at:
// https://www.toptal.com/developers/keycode

```
### CSS
```css
:root[data-theme=" theme1 "]{
    --variable:
    --variable:
    --variable:
}
:root[data-theme=" theme2 "]{
    --variable:
    --variable:
    --variable:
}
// useful color combinations can be sourced from:
// https://www.realtimecolors.com
```


## Feedback

If you have any feedback, feel free to alter the code.

