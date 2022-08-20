# Objects and Maps

### Objects
dot vs square brackets to access object data using keys
If you know that your key is fixed and it is not gonna change, use dot notation. Otherwise, square brackets is best option.

#### Primitives vs Objects
1. Primitives
```
const num = 42
const numTwo = 42
console.log(num === numTwo)
// true , because value is passed
```

2. Objects 
```
const obj1 = {}
const obj2 = {}
console.log(obj1 === obj2)
// false, because referenced is passed not the value
```

```
const obj1 = {}
const obj2 = obj1
console.log(obj1 === obj2)
// true, because when we assigned it to obj2 the referenced is assigned not the actual value
```

#### Object Destructing
It helps accessing the properties much easier and avoid repition.
In normal cases, we will do
```
const obj = {name: "hammad", rollNum: 56, class: 2019}
// If we have to console "hammad is from class of 2019 having roll number 56"
//  we will do like this

console.log(`${obj.name} is from class of ${obj.class} having roll number ${obj.rollNum}`)

```

But OBJECT DESTRUCTING can really help us
```
const obj = {name: "hammad", rollNum: 56, year: 2019}
const {name, rollNum, year} = obj

console.log(`${name} is from class of ${year} having roll number ${rollNum}`)

```

#### Object Vs Array
Objects do not preserve the order of keys. It is objects limitation. Therefore, we use Arrays
Usecase:
If we add elements in objects and now want to remove last element. We should know the key of the last element. Otherwise, there is no way to remove it.
But in case of Arrays, we can use arr.pop() to remove the last element because arrays preserve the order.


### Merging Objects
Two ways
1. assign() method
2. spread operator

1.  assign() takes n number of parameters and merge all of them
```
const obj1 = {name: "hammad", year: 2019, age: 20}
const obj2 = {graduateYear: 2024}
const obj3 = {dataOfBirth: '28 of June'}

const allData = Object.assign(obj1, obj2, obj3)
console.log(allData)

// {name: "hammad", year: 2019, age: 20, graduateYear: 2024, dataOfBirth: "28 of June"}
```

2. Spread Operator
```
const obj1 = {name: "hammad", year: 2019, age: 20}
const obj2 = {graduateYear: 2024}
const obj3 = {dataOfBirth: '28 of June'}

const allData = {...obj1, ...obj2, ...obj3}
console.log(allData)

//  {name: "hammad", year: 2019, age: 20, graduateYear: 2024, dataOfBirth: "28 of June"}
```

***Note***
1. Order matters 
2. Duplicate Properties are removed if they have same values. For different values the value of the property which occurs in last is used.

### Objects Limitations
Object do implicit key convertion to string.
```
const obj = {
	1: 'one',
	false: true
}

// here 1 and false will be treated as strings by JavaScript due to implicit convertion.
```

So, how can we make a key value form in which key is of the type we want?

## Maps is the Answer
maps are objects but solve the above problem and preserve the order too.
Syntax
```
const mapObj = new Map(
    [
			[1, 'value'],
			[2, 'value2']
    ]
)
```

Previous Example
```
cost objMap = new Map(
[
		[1, "one"],
		[false, "true"]
]
)
```

