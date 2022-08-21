# Arrays & Sets
### Arrays

## includes , some and every

#### includes
includes return true or false on basis if given argument is present in array or not.

***Limitation***

*includes* methods on array works only when we are dealing with primitives values. If the data is complex like objects in arrays we cannot use .includes.



#### .some 
So, we can use .some method. It takes a [[callback function]] and return true / false implicitly. The callback function has access to all the elements of array through the provided parameter and we can set the conditional as body of the callback function. It will return ture if at least one element of array fulfilled the condition.

*Example*

```
const temperatures = [
{ degrees: 69, isRecordTemp: false },
{ degrees: 82, isRecordTemp: true },
{ degrees: 73, isRecordTemp: false },
{ degrees: 64, isRecordTemp: false }
];

const result = temperatures.some( temp => {
	temp.isRecordTemp === true
} )

console.log(result)
// true

```

This will return true because temp.isRecordTemp is true for second object.

#### .every 
.every check if the given condition is true for every element of array.

## Manipulating the Array
We can manipulate the array by two methods.
1. map() - return new array of same length
2. forEach()

### Subsets of Array
3. filter() - return new array based on the given condition. (lenght does not matter. )
4. find() - return only one element of the given array

#### map
This method takes a callback and perform the given operations on the element given in body and return the element in new array. 
The new array will have the same lenght.
***Note, if you are using map, must return at the end and store elements in new array***

*Example*
```
const temperatures = [
{ degrees: 69, isRecordTemp: false },
{ degrees: 82, isRecordTemp: true },
{ degrees: 73, isRecordTemp: false },
{ degrees: 64, isRecordTemp: false }
];

const newTemp = temperatures.map(temperatue => {
    return temperatures.degrees > 70 ? [...temperatues, isHigh = true] : temperatue
})

console.log(newTemp)

// [{degrees: 69, isRecordTemp: false}, {degrees: 82, isRecordTemp: true}, {degrees: 73, isRecordTemp: false}, {degrees: 64, isRecordTemp: false}]

```

#### forEach
This method works almost same as map but does not return anything. It just perfoms the given operations on each element of array.

```
let sum = 0
const arr = [1, 2, 3, 4, 5]

arr.forEach(el => {
	sum += el
})

console.log(sum)
// 15
```


#### filter
It works almost same as map but in filter method case it is not necessary that the array length should be equal to original arrays length
It return new array.

```
const arr = [2, 3, 6, 7, 10]

const newArr = arr.filter(el => {
	return el % 2 === 0
})

console.log(newArr)
// [2, 6, 10]

```

***Important Note***
It only returns the element if the condition is true. If we set the condition to true directly it will put all elements in new array.

```
const arr = [2, 3, 6, 7, 10]

const newArr = arr.filter(el => true)

console.log(newArr)
// [2, 3, 6, 7, 10]
```

#### find
works similar to filter but returns only first element where condition is true

```
const arr = [2, 3, 6, 7, 10]

const result = arr.find(el => {
	return el % 2 === 0
})

console.log(result)
```

## reduce()
This is one of the powerfull methods in JavaScript.
This method takes two parameters, a callback and initial value. 
Why it need initial value?
To understand this, let first demystify callback. The callback in reduce takes two parameters, an accumulator and items of array. The initial values given as a second parameter is the initial value of accumulator. 
On first iteration, accumulator = initialValue. 
Body of the callback must have to return a value which will be available for the next iteration.


```
const arr = [1, 2, 3, 4, 5]

const sumArr = arr.reduce((acc, num) => {
	return acc + num
}, 0)

console.log(sumArr)

```

### map method using reduce

```
const temperatures = [
{ degrees: 69, isRecordTemp: false },
{ degrees: 82, isRecordTemp: true },
{ degrees: 73, isRecordTemp: false },
{ degrees: 64, isRecordTemp: false }
];

const mappedArr = temperatues.reduce((acc, temp) => {
	return temp.degrees > 70 ? acc.concat([...temp, isHigh = true]) : acc.concat([temp])
}, [])

console.log(mappedArr)


```


# Arrays Destructing
```
const finalMenuItems = [
  "American Cheeseburger",
  "Southern Fried Chicken",
  "Glazed Salmon"
];

const [first, second, third] = finalMenuItems;
```

Destructing using rest operator
```
const finalMenuItems = [
  "American Cheeseburger",
  "Southern Fried Chicken",
  "Glazed Salmon"
];

const [winner, ...losers] = finalMenuItems;

console.log({ winner, losers });

winner = "American Cheeseburger"
loosers = ["Southern Fried Chicken", "Glazed Salmon"]

```

## ***rest  operator should be at last ***


## Iterating over objects
Can be done using following ways

1. for-in loop 
```
// for-in loop

const obj = { one: 1, two: 2 };
for (const key in obj) {
  console.log('value', obj[key]);
}
```
2. Object.keys(objName)
This returns all the keys of array and we can check if certain key exist or not using this
```
const user = {
  name: 'John',
  age: 29  
};

const keysArr = Object.keys(user)
console.log(keysArr.includes("name"))
```
4. Object.values(objName)
This returns all the values of the keys
```
const user = {
  name: 'John',
  age: 29  
};

Object.keys(user).map((properties) => {
    console.log(user[properties])
})

// 'John'
// 29
```
5. Object.entries(objName)
This returns both the keys and values in form of 2d array
```
const user = {
  name: 'John',
  age: 29  
};

console.log(Object.entries(user))
// [["name", "John"], ["age", 29]]
```

Explain this code with the output

```
const users = {
  '2345234': {
    name: "John",
    age: 29
  },
  '8798129': {
    name: "Jane",
    age: 42
  },
  '1092384': {
    name: "Fred",
    age: 17 
  }
};

const usersOver20 = Object.entries(users).reduce((acc, [id, user]) => {
  if (user.age > 20) {
    acc.push({ ...user, id });
  }  
  return acc;
}, []);
console.log(usersOver20);
```

# Sets
converting array to set and back to array

```
const customerDishes = [
  "Chicken Wings",
  "Fish Sandwich",
  "Beef Stroganoff",
  "Grilled Cheese",
  "Blue Cheese Salad",
  "Chicken Wings",
  "Reuben Sandwich",
  "Grilled Cheese",
  "Fish Sandwich",
  "Chicken Pot Pie",
  "Fish Sandwich",
  "Beef Stroganoff"
];

const uniqueDishes = [...new Set(customerDishes)];
console.log(uniqueDishes)

// ["Chicken Wings", "Fish Sandwich", "Beef Stroganoff", "Grilled Cheese", "Blue Cheese Salad", "Reuben Sandwich", "Chicken Pot Pie"]


```

### Iterating over sets

```
const numbers = new Set([[1], [2], [3]]);

for (const num of numbers) {
	console.log(num);  
}
```
***note***
as objects are passed by reference and their values cannot be compared. Therefore, two objects/ arrays with same properties or values cannot be compared and set will not consider them same.


# Take grip on these
```
/* 
- map()
- filter()
- reduce()
- some() / every()
- find() / findIndex()
- forEach()

Plus:

- slice()
- concat()
- includes()
- array spread operator
*/
```
