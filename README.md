<p align="center">
  <label style="font-weight:bold;font-size:x-large">Transform SVG to React Chakra UI <Icon \/> ✨ </label>
  <br/><label style="font-weight:bold;font-size:small">from SVG file to CODE</label>
  <br/>
  <br/>
  <img src="https://github.com/kodingdotninja/create-chakra-icons/blob/main/create-chakra-icons.gif?raw=true" alt="creater-chakra-icons" />  
</p>


## Features
* [x] Transform `<SVG/>` to Chakra-UI `Icon` Component or Functional `createIcon(...)`.
* [x] Multiple input with `directories` as `-i` or `--input` options

## Usage

### CLI

```console
npx create-chakra-icons -n "MyIcon" -i ./myicon.svg -o ./MyIcon.js
```

### Options

*   `-n/--name`:  it will be `displayName` in Component Properties.
*   `-i/--input`:  where your put the `SVG` file - can be `file` or `directories`.
*   `-o/--output`: where your want to save your file.

### Pipe (stdout)

```console
$> echo "
<svg viewBox=\"0 0 200 200\">
    <path
      fill=\"#666\"
      d=\"M 100, 100 m -75, 0 a 75,75 0 1,0 150,0 a 75,75 0 1,0 -150,0\"
    />
  </svg>
" | create-chakra-icons -n "Rin"
// output
import { createIcon } from "@chakra-ui/react";
export const Rin = createIcon({
  displayName: "Rin",
  viewBox: "0 0 200 200",
  d: "M 100, 100 m -75, 0 a 75,75 0 1,0 150,0 a 75,75 0 1,0 -150,0"
});
```

### Pipe (output file)

```console
$> echo "
<svg viewBox=\"0 0 200 200\">
    <path
      fill=\"#666\"
      d=\"M 100, 100 m -75, 0 a 75,75 0 1,0 150,0 a 75,75 0 1,0 -150,0\"
    />
  </svg>
" | create-chakra-icons -n "Rin" > RinIcon.js 
```

## Readmap

* [ ] TypeScript Support (Type Annotation or Type Definition).
* [ ] ReScript Support.
* [ ] Per file input is Per file output. ⁉️ 🤔
* [ ] Feel free for give me any feedback or feature request (create an issue first).


## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

#### Table of Contents

*   [ast](#ast)
    *   [pairToObjectProperty](#pairtoobjectproperty)
        *   [Examples](#examples)
    *   [objectPropertyToPair](#objectpropertytopair)
        *   [Parameters](#parameters)
        *   [Examples](#examples-1)
    *   [objectToObjectExpression](#objecttoobjectexpression)
        *   [Parameters](#parameters-1)
        *   [Examples](#examples-2)
    *   [objectExpressionToObject](#objectexpressiontoobject)
        *   [Parameters](#parameters-2)
        *   [Examples](#examples-3)
    *   [toImportDeclaration](#toimportdeclaration)
        *   [Parameters](#parameters-3)
    *   [toExportNamedDeclaration](#toexportnameddeclaration)
        *   [Parameters](#parameters-4)
        *   [Properties](#properties)
        *   [Examples](#examples-4)
    *   [toSource](#tosource)
        *   [Parameters](#parameters-5)
    *   [hastToProperties](#hasttoproperties)
        *   [Parameters](#parameters-6)
    *   [hastChildrenLength](#hastchildrenlength)
        *   [Parameters](#parameters-7)
    *   [hastToJSXProperties](#hasttojsxproperties)
        *   [Parameters](#parameters-8)
    *   [jsxPropertiesToComponent](#jsxpropertiestocomponent)
        *   [Parameters](#parameters-9)
*   [objectToObjectExpression](#objecttoobjectexpression-1)
    *   [Parameters](#parameters-10)
*   [chakra](#chakra)
    *   [createChakraIcon](#createchakraicon)
        *   [Parameters](#parameters-11)
*   [utils](#utils)
    *   [compose](#compose)
        *   [Parameters](#parameters-12)
    *   [pairToObject](#pairtoobject)
        *   [Parameters](#parameters-13)
    *   [objectToPair](#objecttopair)
        *   [Parameters](#parameters-14)
    *   [pairsToObject](#pairstoobject)
        *   [Parameters](#parameters-15)
    *   [objectToPairs](#objecttopairs)
        *   [Parameters](#parameters-16)

### ast

#### pairToObjectProperty

##### Examples

```javascript
const pair = ["hey", "jude"]

pairToObjectProperty(value)
// output:
// {
//   type: 'ObjectProperty',
//   key: { type: 'Identifier', name: 'hey' },
//   value: { type: 'StringLiteral', value: 'jude' },
//   computed: false,
//   shorthand: false,
//   decorators: null
// }
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

#### objectPropertyToPair

##### Parameters

*   `Object`  

##### Examples

```javascript
const objectProperty = {
  type: 'ObjectProperty',
  key: { type: 'Identifier', name: 'hey' },
  value: { type: 'StringLiteral', value: 'jude' },
  computed: false,
  shorthand: false,
  decorators: null
}

objectPropertyToPair(objectProperty)
// output: ["hey", "jude"]
```

Returns **\[[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String), [String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)]** 

#### objectToObjectExpression

##### Parameters

*   `Object`  

##### Examples

```javascript
let object = { hey: "jude" }
// output:
objectToObjectExpression(object)
// {
//   type: 'ObjectExpression',
//   properties: [
//     {
//       type: 'ObjectProperty',
//       key: [Object],
//       value: [Object],
//       computed: false,
//       shorthand: false,
//       decorators: null
//     }
//   ]
// }
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

#### objectExpressionToObject

##### Parameters

*   `Object`  

##### Examples

```javascript
let objectExpression = {
  type: 'ObjectExpression',
  properties: [
    {
      type: 'ObjectProperty',
      key: [Object],
      value: [Object],
      computed: false,
      shorthand: false,
      decorators: null
    }
  ]
}
objectExpressionToObject(objectExpression)
// output:
// let object = { hey: "jude" }
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

#### toImportDeclaration

*   **See**: {<https://babeljs.io/docs/en/babel-types#importdeclaration}>

##### Parameters

*   `from` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** 
*   `imports` **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)<[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)>** 

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

#### toExportNamedDeclaration

##### Parameters

*   `Object`  

##### Properties

*   `displayName` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** 
*   `objectExpression` **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

##### Examples

```javascript
let object = {
 displayName: "MyModule",
 objectExpression: {...} // you can make with function objectToObjectExpression
}
toExportNamedDeclaration(object)
```

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

#### toSource

##### Parameters

*   `Array`  

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

#### hastToProperties

##### Parameters

*   `Object`  

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

#### hastChildrenLength

##### Parameters

*   `Object`  

Returns **[Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number)** 

#### hastToJSXProperties

##### Parameters

*   `Object`  

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

#### jsxPropertiesToComponent

##### Parameters

*   `Object`  

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

### objectToObjectExpression

#### Parameters

*   `object`  

### chakra

the module for generate Chakra Icon Code.

#### createChakraIcon

##### Parameters

*   `svg` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** 
*   `displayName` **[String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String)** 

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

### utils

provided utility function.

#### compose

##### Parameters

*   `Array`  

Returns **T** 

#### pairToObject

##### Parameters

*   `Array`  

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

#### objectToPair

##### Parameters

*   `Object`  

Returns **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)** 

#### pairsToObject

##### Parameters

*   `Array`  

Returns **[Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object)** 

#### objectToPairs

##### Parameters

*   `Object`  

Returns **[Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array)** 

## Contribution

Feel free for making an issue, pull request, or give any feedback. 🙌

### Documentation

*   Write the documentation 📝, you just need to modify `comments` in `lib/*.js`.
*   When you done write the documentation, you just need to run `yarn docs` in the root repository.
*   The command `yarn docs` will modify `README.md` and see the changes.

## LICENSE

[See Here](./LICENSE)
