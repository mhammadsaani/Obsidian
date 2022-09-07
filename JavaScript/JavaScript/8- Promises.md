## Promises 
***callbacks -> promises***
States of Promises

1.  pending (By Default State)
2.  fulfilled
3.  rejected

**Promise** is sort of buzer which tells us the status of our async code whether it is fulfilled, rejected or pending. and meanwhile it is pending, we can do whatever we want to do and when our promise is resolved, we can do with the result whatever we want to do.

Why Promises over Callbacks?
*Promises* are powerfull because they give us the control to over a certain async execution which we cannot control via Callbacks

// Promises takes a callback as an argument which gives us control. The callback accept two parameters (resolve, reject). By default, the promise has pending state and we can change the state using these two parameters which are functions. 

```
const a = 10
const b = 20
const testPromise = new Promise((resolve, reject) => {
	if(a === b){
		return resolve("Promise Resolved and a === b")
	}
	return reject(Error("Promise Rejected"))
})

testPromise.then(data => console.log(data)).catch(err => console.error(err))
```

1. Resolve alows you to change the status to fulfilled  
2. Reject allows u to change the state to rejected.

Our instance of Promise is an object and two methods can be chained on it. .then() and .catch().
// .then and .catch takes a callback. 
// .then is executed when resolve is called inside the instance of the Promise and .catch() is called when reject() is called inside the instance of promise.  There is also a method after .catch(), .finally() which tells either the rejected / fulfilled state is executed and promise is over.