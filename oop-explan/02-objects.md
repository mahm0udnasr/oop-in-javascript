## خد بالك إن جافاسكريبت كل اللي فيها في الآخر بيكون `object`، فقبل ما نتعلم OOP لازم نتعرف الأول على الـ objects بشكل كويس جداً.

### إن شاء الله هنغطي المفاهيم الأساسية للـ objects.

### خدلك نظرة سريعة على العناوين اللي هنشرحها، لو لقيت نفسك عارفها ادخل على اللي بعده على طول لو عاوز توفر وقت.

---

##  1. Creating Objects

```js
const person = {
	name: "Mahmoud",
	address: {
		1: "Tanta",
		2: "Egypt"
	},
	getInfo: function() {
		console.log(`Hello there, I'm ${this.name} from ${this.address[1]}, ${this.address[2]}`);
	}
}
person.getInfo();
```

##  3. Constructor Functions

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