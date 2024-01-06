# IonicSDK for ionic 5.x

## How to use?

- Clone your repository  
`git clone <your repository url>`

- Create a new branch
- Add IonicSDK repo URL to remote  
`git remote add ionicSDK https://github.com/hotwax/ionic-sdk.git`

- Fetch IonicSDK branches  
`git fetch ionicSDK`

- Merge IonicSDK master to your branch with [--allow-unrelated-histories](https://git-scm.com/docs/git-merge#Documentation/git-merge.txt---allow-unrelated-histories) flag  
`git merge ionicSDK/master --allow-unrelated-histories`

- Resolve conflicts  
- Push your branch and create a PR

## Firebase Hosting

We are using firebase hosting for the Pre-order app deployment
Here are the steps to deploy app on firebase hosting

### Prerequisite
- [Firebase Cli](https://firebase.google.com/docs/cli) should be installed 
- Firebase project should be created
- You should have access to firebase project

### Dev deployment 
- Update the DEV instance url at .env.production file

- Build the application using following command
`ionic build`

- Login into firebase 
`firebase login`

- Run following command to deploy to firebase hosting
`firebase deploy --only hosting:sm-dev`


### UAT deployment 
- Update the UAT instance url at .env.production file

- Build the application using following command
`ionic build`

- Login into firebase 
`firebase login`

- Run following command to deploy to firebase hosting
`firebase deploy --only hosting:sm-uat`


## How to build application in different environment or modes(staging, production, qa, etc)?
As there is a bug in Ionic cli due to which we cannot pass flag variables for commands (See [#4669](https://github.com/ionic-team/ionic-cli/issues/4642)). To build application in different modes we need to use vue-cli-service to build and then use the built app using capacitor copy command further. 

Follow following instructions:
1. Manually build the application using vue-cli-service:
npx vue-cli-service build --mode=sandbox

2. Copy web assets to the native project without building the app:
ionic capacitor copy ios --no-build

3. Open the Android Studio / XCode project:
ionic capacitor open android   
ionic capacitor open ios

## Coding Style Guide
### Semicolon
A semicolon is not necessary after end of statement in JS. But in some cases, semicolons are required which are handled by Automatic Semicolon Insertion(ASI) while parsing the code.

There are some cases in which you always need to add a semicolon, otherwise will lead to an exception.
```js


```

### Spacing
1. Use tabs for indentation set to 2 spaces

```js
// Bad ❌
function foo() {  
****let bar
}

function foo() {
let bar
}

// Good ✅
function foo() {
**let bar
}
```

2. A whitespace should be added before an opening brace `{`.
```js
// Bad ❌
function foo(){
  ...do something
}

// Good ✅
function foo() {
  ...do something
}
```

3. A whitespace should be added before opening paranthesis `(` in control statements(while, if, for etc), and should not add any whitespace before opening paranthesis(`(`) in function calls, declarations, and arguments.
```js
// Bad ❌
function foo () {
  ...do something
}

// Good ✅
function foo() {
  ...do something
}

// Bad ❌
foo ()  // function call

// Good ✅
foo()  // function call

// Bad ❌
if(condition)

for(condition)

// Good ✅
if (condition)

for (condition)
```

4. No whitespace before a semicolon, if used.
```js
// Bad ❌
let foo ;

// Good ✅
let foo;
```

5. Add an empty line after a code block ends
```js
// Bad  ❌
function foo {
  return;
}
let bar = 'string'

// Good ✅
function foo {
  return;
}

let bar = 'string'
```

6. Operators should always have whitespaces around
```js
// Bad ❌
let bar=foo+bar

// Good ✅
let bar = foo + bar
```

7. Add whitespaces inside curly braces.
```js
// Bad ❌
let foo = {"key": "value"}

// Good ✅
let foo = { "key": "value" }
```

8. Do not include spaces inside brackets `[]`.
```js
// Bad ❌
let foo = [ 1, 2, 3 ]

// Good ✅
let foo = [1, 2, 3]
```

9. Use single character to define EOF.

10. Avoid including trailing spaces at the end of lines.
```js
// Bad ❌
let foo = "name"**

// Good ✅
let foo = "name"
```

11. Avoid using whitespace before comma, but should have whitespace after the comma, if followed by other values in the same line

```js
// Bad ❌
let foo = ["a" , "b" , "c"]
let foo = ["a" ,"b" ,"c"]
let foo = ["a", ]

// Good ✅
let foo = ["a", "b", "c"]
let foo = ["a",]
```


```js
// Bad ❌
// Good ✅
```

### String
Use Double quotes("") for declaring string and use Single quotes('') for string which is already enclosed in Double quotes("").

Why using Double quotes for string declaration?
In JavaScript, string can be both declared with double("") or single('') quotes, as using the one depends, there is no standard defined for the usage of one over the other. But when declaring a JSON object a string needs to be in double quotes("") and hence using double quotes for strings in JS, as we use JSON in most of the cases, so that its simpler when dealing with JSON in JS.

```js
// Use double quotes, do not use interpolation to declare strings
// Bad ❌
let sample = 'name'
let sample = `name`

// Good ✅
let sample = "name"

// Declaring a string inside ""

// Bad ❌
onClick="save('name')"

// Good ✅
onClick='save("name")'

// Use interpolation when creating dynamic string using variables

// Bad ❌
let sample = "This is a " + sample

// Good ✅
let sample = `This is a ${sample}`
```

### Naming Conventions

File naming
Component naming
Variable naming
Function naming
