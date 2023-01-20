# iOS-Friendly Web Dev

### About this project

iOS-compatible web development presents many unique challenges.

This is a community-maintained repository for keeping track of iOS/Safari/WebKit quirks and potential workarounds for web developers.

### How to contribute

This repository is a community effort. Pull requests and suggestions for improvements are welcome.

Please submit a pull request to:
- Add a quirk to the list
- Add to or clarify an existing quirk
- Remove incorrect or outdated information

# Quirks

## Font size affects button padding

- **Reported date:** 20th Jan 2023
- **Description:** The padding-left and padding-right properties of buttons are affected by the button's font size. If you don't specify these values, Safari on iOS will render your button with unexpected padding.
- **Possible solution:** Explicitly define padding for all button elements.
```CSS
button {
    padding: 0;
}
```

## Window:resize event triggers on scroll

- **Reported date:** 20th Jan 2023
- **Description:** Scrolling on a page in Safari on iOS triggers the window:resize event.
- **Possible solution:** Get the window's width and/or height when your JS code is first run. Then, for your function which is triggered by the "resize" event listener, add an if statement to check if the window has truly been resized or just scrolled.
```JavaScript
let startingWidth = window.innerWidth;

window.addEventListener("resize", example);

function example() {
    if (startingWidth != window.innerWidth) {
        console.log("It has been resized!");
    } else {
        return;
    }
}
```

## Phone numbers render as links

- **Reported date:** 20th Jan 2023
- **Description:** Safari on iOS automatically transforms phone numbers into links.
- **Possible solution:** Use a meta tag to stop the transformation.
```HTML
<meta name="format-detection" content="telephone=no"/>
```
