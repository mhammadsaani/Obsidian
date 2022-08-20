# Conditionals
### Tips
1. Use strict mode to avoid pitfalls of language
	``` 
	'use strict'
	```
2. Avoid Direct Comparisons
	```
	const username = ''
	// Do not do this
	if (username === false){
		
		}
	
	// instead do this

	if (!username){
	
	}
	```
3. Use triple equals (strict equal operator)
	```
	if (null == undefined){
		// this will run
	}

	// therefore, use this

	if (null === undefined){
		// now this will not run
	}

	```

4. Convert to real Boolean Values When Needed
Sometimes, you need to convert the expressions to Boolean.

```
NaN === NaN // will give false
therefore, 
Boolean(NaN) === Boolean(NaN) // will give true
```

5. Ternary Syntax

const result = (condition) ? if ture : else 
6. Short Circuiting 
	 Use of logical operator to make conditionals shorter

```
This code will evaluate to ?  

const response = "Reed";
const isEmailVerified = true;
const username = isEmailVerified && response || "guest";
console.log(username);

explain it too?
```
*Explanation*
This will evaluate to "Reed"
