## Factory Functions

```js
// Factory Function
function createPerson(name) {
	return {
		name,
		sayHello: function() {
			console.log(`Hello I'm ${this.name}`);
		}
	}
}

const personOne = createPerson("Mahmoud");
const personTwo = createPerson("Ahmed");
const personThree = createPerson("Ali");

personOne.sayHello();
personTwo.sayHello();
personThree.sayHello();
```