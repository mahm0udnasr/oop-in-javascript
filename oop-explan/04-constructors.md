## Constructor Functions

```js
// Constructor Function
function Person(name, gender, birthYear) {
	this.name = name;
	this.gender = gender;
	this.birthYear = birthYear;
	this.calcAge = function() {
		return new Date().getFullYear() - this.birthYear;
	};
}

const personOne = new Person("Mahmoud", "Male", 2005);
console.table(personOne); // Mahmoud | Male | 2005
console.log(personOne.calcAge()); // 20
```