# yaml2json JavaScript (browser only)

http://yamltojson.com/

Downloaded [yaml.js](http://yamltojson.com/js/yaml.js) and changed to `yaml2json.js`

`<script src="http://yamltojson.com/js/yaml.js"></script>`
```

(function () {
  "use strict";

  var YAML = window.YAML
    , json
    , data
    , yml
    ;

  yml = '---\n  foo: bar';
  data = YAML.parse(yml);
  json = JSON.stringify(data);

  console.log(json);
}());
```
* [JSON.stringify](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)
* [YAML.parse](https://github.com/jeremyfa/yaml.js)


# json2yaml JavaScript (browser only)

http://jsontoyaml.com/

Downloaded [json2yaml.js](http://jsontoyaml.com/js/json2yaml.js) and changed to `json2yaml.js`

`<script src="http://jsontoyaml.com/js/json2yaml.js"></script>`
```
(function () {
  "use strict";

  var YAML = window.YAML
    , json
    , data
    , yml
    ;

  json = '{ "foo": "bar" }';
  data = JSON.parse(json);
  yml = YAML.stringify(data);

  console.log(yml);
}());
```
* [JSON.parse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)
* [YAML.stringify](https://github.com/coolaj86/json2yaml)
