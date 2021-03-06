<h1 align="center">QUESON</h1>
<p align="center"><em><strong>QUE</strong>ry, <strong>U</strong>RL-<strong>E</strong>ncodable <strong>E</strong>CMA<strong>S</strong>cript <strong>O</strong>bject <strong>N</strong>otation</em></p>

<p align="center"><a href="https://tcard.github.io/queson/live">Online live compiler</a> | <a href="#implementations">Implementations</a></p>

<hr>

**QUESON** is a **URL-friendly** alternative notation for **JSON**.

This JSON:

```json
{
  "Hello!": ["It looks", "like this."],
  "Kind of weird": {
    "but better than": "the alternative!"  
  }
}
```

which minified and URL-encoded looks like this:

```
%7B%22Hello%21%22%3A%5B%22It%20looks%22%2C%22like%20this.%22%5D%2C%22Kind%20of%20weird%22%3A%7B%22but%20better%20than%22%3A%22the%20alternative%21%22%7D%7D
```

in QUESON, looks like this instead:

```
X.w.Hello!.w-I.w.It_looks.w_w.like_this...w.I_w.Kind_of_weird.w-X.w.but_better_than.w-w.the_alternative!.w.X.X
```

* Strings are enclosed in `w.` `.w`  (because `w` kind of looks like `"`).
* Arrays are enclosed in `I.` `.I` (because `I` kind of looks like `[` and `]`), with elements separated by `_`.
* Objects are enclosed in `X.` `.X` (because `X` kind of looks like `{` and `}`), with keys separated from values by `-`, and properties separated by `_`.
* Spaces in strings are represented as `_`; the escape character is `.`.
* Numbers, booleans and null stay mostly the same.

## Implementations

* [Go](https://github.com/tcard/queson-go)
* [JavaScript](https://github.com/tcard/queson-js)

## Specification

There's a [PEG.js](https://pegjs.org/) grammar that produces a JSON string that serves as spec:

[queson2json.pegjs](https://github.com/tcard/queson-js/blob/main/queson2json.pegjs)

## Design and alternatives

There are multiple alternatives for URL-friendly JSON representations:

* [URLON](https://github.com/cerebral/urlon)
* [qs](https://www.npmjs.com/package/qs)
* [Rison](https://rison.io/)

QUESON is different because:

* A QUESON value fits in a single query parameter, so you can use other query parameters.
* QUESON delimiters don't need percent-encoding, so the structure _can_ be legible by a human, if you squint (most non-alphanumerical characters inside strings will get percent-encoded, though). 
