# QUESON

**QUE**ry, **U**RL-**E**ncodable **E**CMA**S**cript Object Notation

QUESON is a URL-friendly alternative notation for JSON.

* Strings are enclosed in `w.` `.w`  (because `w` kind of looks like `"`).
* Arrays are enclosed in `I.` `.I` (because `I` kind of looks like `[` and `]`), with elements separated by `_`.
* Objects are enclosed in `X.` `.X` (because `X` kind of looks like `{` and `}`), with keys separated from values by `-`, and properties separated by `_`.
* Spaces in strings are represented as `_`; the escape character is `.`.
* Numbers, booleans and null stay mostly the same.

So this JSON:

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

## Implementations

* [Go](https://github.com/tcard/queson-go)
* [JavaScript](https://github.com/tcard/queson-js)
