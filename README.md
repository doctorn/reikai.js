#reikai.js
JavaScript library for creating and displaying example Go boards

##About
`reikai.js` was created as part of the [Cambridge University Go Society](http://cugosoc.soc.srcf.net/) website redesign. In legacy versions of the site, example boards had been stitched together out of small elements each the size of one grid square on a Go board. This resulted in hundreds of `img` tags to produce a single board. To solve this, `reikai.js` allows for boards to be described in a simple JSON format and then rendered to an HTML5 canvas. This means that a board can be embedded using a single `div` tag.

##Usage
A hosted version of `reikai.js` is available at [`http://cugosoc.soc.srcf.net/static/reikai.js`](http://cugosoc.soc.srcf.net/static/reikai.js) and can therefore be embedded as follows.

```html
<script type="text/javascript" src="http://cugosoc.soc.srcf.net/static/reikai.js"></script>
```

To then embed a board, first create a JSON file of the following form.

```json
{
  "size": 19,
  "start": {
    "x": 0,
    "y": 0
  },
  "end": {
    "x": 18,
    "y": 18
  },
  "stones": [
    {
      "x": 4, 
      "y": 4,
      "black": true,
      "label": "1"
    } 
  ]
}
```

`size` represents the dimensions of the board. The supported values are `9`, `13` and `19`. 

`start` represents the coordinate that will appear in the upper left of the board.

`end` represents the coordinate that will appear in the bottom right of the board. `end.x` must be greater than `start.x` and `end.y` must be greater than `start.y`.

_Note that all coordinates are 0 indexed._

`stones` contains an array of stone objects. Each stone has a coordinate (given by `x` and `y`); a boolean, `black`, which should be `true` if the stone is to be black and `false` if it is to be white; and an optional label, `label`, which may be any string (although strings of more than two characters do not render correctly).

Assuming that this JSON is then hosted at `http://example.com` as `example_reikai.json`, embed the board into our page as follows.

```html
<div class="reikai_board" data_board="http://example.com/example_reikai.json"></div>
```

Finally, on page load call `reikai.init()` to trigger the boards to be loaded. A typical example would be as follows.

```html
<div class="reikai_board" data_board="http://example.com/example_reikai.json"></div>
<script type="text/javascript">
  (function() {
    reikai.init(); 
  })();
</script>
```

##Feedback
Issue reports and feedback are welcome.
