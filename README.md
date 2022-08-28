# code-tips-javascript
Code tips for clean code in Javascript

## Use the same vocabulary for the same concept

```javascript
// Bad

getUserInfo();
getClientData();
getCustomerRecord();


// Good

getUser();
```

## Use pronounceable and meaningful variable names

```javascript
// Bad

const yyyymmdstr = moment().format("YYYY/MM/DD");


// Good

const currentDate = moment().format("YYYY/MM/DD");
```

## Avoid Mental Mapping

```javascript
// Bad

const locations = ["Austin", "New York", "San Francisco"];
locations.forEach(l => {
  doStuff();
  // Wait, what is `l` for again?
  dispatch(l);
});

// Good

const locations = ["Austin", "New York", "San Francisco"];
locations.forEach(location => {
  doStuff();
  dispatch(location);
});
```

## Few Function Arguments

```javascript
// Bad

function createMenu(title, body, buttonText, cancellable) {
  // ...
}
createMenu("Foo", "Bar", "Baz", true);


// Good

function createMenu({ title, body, buttonText, cancellable }) {
  // ...
}
createMenu({
  title: "Foo",
  body: "Bar",
  buttonText: "Baz",
  cancellable: true
});
```

## Don’t Use Magic Numbers

```javascript
// Bad

setTimeout(blastOff, 86400000); // What is 86400000?


// Good 

// Declare them as capitalized named constants.
const MILLISECONDS_PER_DAY = 60 * 60 * 24 * 1000; //86400000;
setTimeout(blastOff, MILLISECONDS_PER_DAY);
```

##  Use Explanatory Varibles

```javascript
// Bad

const address = "One Infinite Loop, Cupertino 95014";
const cityZipCodeRegex = /^[^,\\]+[,\\\s]+(.+?)\s*(\d{5})?$/;
saveCityZipCode(
  address.match(cityZipCodeRegex)[1],
  address.match(cityZipCodeRegex)[2]
);


// Good

const address = "One Infinite Loop, Cupertino 95014";
const cityZipCodeRegex = /^[^,\\]+[,\\\s]+(.+?)\s*(\d{5})?$/;
const [_, city, zipCode] = address.match(cityZipCodeRegex) || [];
saveCityZipCode(city, zipCode);
```

## Don't add unneeded context

```javascript
// Bad

const Car = {
  carMake: "Honda",
  carModel: "Accord",
  carColor: "Blue"
};


// Good

const Car = {
  make: "Honda",
  model: "Accord",
  color: "Blue"
};
```

## Functions should do one thing

```javascript
// Bad

function emailClients(clients) {
  clients.forEach(client => {
    const clientRecord = database.lookup(client);
    if (clientRecord.isActive()) {
      email(client);
    }
  });
}


// Good 

function emailActiveClients(clients) {
  clients.filter(isActiveClient).forEach(email);
}
function isActiveClient(client) {
  const clientRecord = database.lookup(client);
  return clientRecord.isActive();
}
```

## Function names should say what they do

```javascript
// Bad

function addToDate(date, month) {
  // ...
}
const date = new Date();
// It's hard to tell from the function name what is added
addToDate(date, 1);

// Good

function addMonthToDate(month, date) {
  // ...
}
const date = new Date();
addMonthToDate(1, date);
```

## Encapsulate Conditionals

```javascript
// Bad

if (fsm.state === "fetching" && isEmpty(listNode)){
	// ...
}


//Good

function shouldShowSpinner(fsm, listNode) {
	return fsm.state === "fetching" && isEmpty(listNode);
}

if (shouldShowSpinner(fsmInstance, listNodeInstance)){
	// ...
}
```

## Remove Dead Code
```javascript
// Bad

function oldRequestModule(url){
	// ...
}
function newRequestModule(url){
	// ...
}


// Good

function newRequestModule(url){
	// ...
}
```
