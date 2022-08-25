# Classes
### Contructor function
It is special function that helps us to make a sort of template from which we can make objects which have the same properties as the template has.

*Example*
```
const student = {
	name: "hammad",
	id: 56,
	subjects: [],
	addSubject(subject){
		this.subjects = [...this.subjects, subject]
	}
}

student.addSubject("Physics")
console.log(student.subjects)

```

Here the issue is that if we need to add more students, we will have to write properties for every object every time with function. But we have a way to avoid this

**Constructor Function**
```
Function Student(name, id, subjects = []){
	this.name = name,
	this.id   = id,
	this.subjects = subjects
}
```
Constructor function work as a template and is used to make students in this case.

```
const student1 = new Student('Reed', 1);
const student2 = new Student('Doug', 2);
```

Now, two students will be generated with `id and name`
we can add more methods and properties using
```
Student.prototype.addSubject = function(subject){
	this.subjects = [...this.subjects, subject]
}
```

Setting and priting the subjects values
```
student1.addSubject('Math');
student2.addSubject('Physics');
console.log(student1.subjects);
console.log(student2.subjects);

// Math
// Physics
```

### Understanding the Prototype Chain
**Prototype Defintion**
 - Every object in JavaScript has a built-in property, which is called its prototype

1. `prototypical inheritance - each instantiated object (from constructor function) inherits from prototype
2. `every object has prototype`


```
function Student(id, name, subjects = []) {
  this.id = id;
  this.name = name;
  this.subjects = subjects;
}

const student1 = new Student(1, 'Reed');

console.log(Object.getPrototypeOf(student1).constructor);
console.log(student1.__proto__);
```

### Constructor vs Classes
1. classes === constructor functions (they operate in same way)
2. classes - create objects with shared methods
3. functions declared in contructors are not propertes. So, cannot be accessed using `Student.functionName()` syntax

```
class Student {
  constructor(id, name, subjects = []) {
    this.id = id;
    this.name = name;
    this.subjects = subjects;      
  }  
    
  getStudentName() {
    return `Student: ${this.name}`  
  }
    
  addSubject() {}  
}

const student1 = new Student(1, 'Reed');
console.log(student1.getStudentName());

```

### Extending a class Syntax
```
class Product {
  constructor(name, price, discountable) {
    this.name = name;
    this.price = price;
    this.discountable = discountable;  
  }  
  
  isDiscountable() {
    return this.discountable;  
  }
}

class SaleProduct extends Product {
  constructor(name, price, discountable, percentOff) {
     super(name, price, discountable);
     this.percentOff = percentOff; 
  }  
  
  getSalePrice() {
     if (super.isDiscountable()) {
       return this.price * ((100 - this.percentOff) / 100);
     } else {
        return `${this.name} is not eligible for a discount`;
     }
  }
}

const saleProduct1 = new SaleProduct("Coffee Maker", 99, true, 20);
console.log(saleProduct1.getSalePrice());
```



Classes Advance Concepts

