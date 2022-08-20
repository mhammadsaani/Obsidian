# Functions
### Closures
1. Closures are a property of JavaScript Functions
2. Call Functions in different scope than where function was original defined

### Explanation
Closure help us remember values that lies in function and then change it outside of that function scope

### Example
In closure, function is returned which have the variable value, we want to update. Then we call that function which is returned and can update the value.  
  

```
 
function handleLikePost() {
	let likeCount = 0;
	return function addLike() {
		likeCount += 1;
		return likeCount;
	}
}

const like = handleLikePost();
console.log(like());
console.log(like());
console.log(like());
```

### Closure with respect to a Object setter / getter
Closure is bascially same concept as of a variable declared in a class and we can access the variable with some method in class and then update it.  
So, everytime, the update method will be called, the value of that variable will get update
