> [!tip]
The **`delete`** operator removes a property from an object. 
If the property's value is an object and there are no more references to the object, 
the object held by that property is eventually released automatically.

```javascript
let test = {a:0, b:1, c:2}; 
delete test.a; 
console.log(test);

delete object.property
delete object[property] // 객체의 키값에 접근하는 방법중 하나;
```

- `name` : 객체의 키값;
- 삭제하고 그 키 값으로 접근할 때, 속성값은 `undefined`를 반환한다.

```javascript
const Employee = {
  firstname: 'John',
  lastname: 'Doe',
};

console.log(Employee.firstname);
// Expected output: "John"

delete Employee.firstname;

console.log(Employee.firstname);
// Expected output: undefined
```

- `delete a.name` -> `true`를 리턴한다.
- ex)
```javascript
const person = {
	name:'kim'
}

const deleteNameSuccess = delete person.name; //또는 delete person['name'];
console.log(deleteNameSuccess); // true

const deleteAgeSuccess = delete person.age; //또는 delete person['age'];
console.log(deleteAgeSucceess); // true

// 그러나 빌트인 객체의 속성이나, 변수를 삭제하려고 할때는 false를 리턴한다.
```

- 배열에서의 
```javascript
const trees = ["redwood", "bay", "cedar", "oak", "maple"];
delete trees[3];
console.log(trees); // ["redwood", "bay", "cedar", empty, "maple"];
// index 는 유지되지만, length가 달라진다.
console.log(3 in trees); // false

// 객체
const person = {
	name:'kimkr',
	age:36,
	address:'seoul'
}
delete person.address //or delete person['address'];

console.log(person);
// {
//	name:'kimkr',
//	age:36
// }

console.log('name' in person) // true;
console.log('address' in person) // false
```
- 위의 예제에서의 [[in]]에 대하여...

### 객체 보호 [[Object.defineProperty]]
```javascript
const Employee = {};
Object.defineProperty(Employee, "name", { configurable: false });

console.log(delete Employee.name); // returns false
```

#### 프로토타입 [[prototype]]에서의 delete
```javascript
function Foo() {
  this.bar = 10;
}

Foo.prototype.bar = 42;

const foo = new Foo();

// foo.bar is associated with the
// own property.
console.log(foo.bar); // 10

// Delete the own property within the
// foo object.
delete foo.bar; // returns true

// foo.bar is still available in the
// prototype chain.
console.log(foo.bar); // 42

// Delete the property on the prototype.
delete Foo.prototype.bar; // returns true

// The "bar" property can no longer be
// inherited from Foo since it has been
// deleted.
console.log(foo.bar); // undefined
```