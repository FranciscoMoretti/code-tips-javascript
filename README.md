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
