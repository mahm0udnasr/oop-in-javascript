# 🎓 JavaScript Classes

الـ **Classes** في JavaScript هي مجرد طريقة جديدة (Syntax حديث) لتعريف كائنات (Objects) ووراثة (Inheritance)، وهي في الأساس بتشتغل فوق نظام الـ **Prototype** بس بشكل أسهل وأوضح.

---

## 🧱 1. يعني إيه Class؟

الـ `class` هي قالب (Template) بنستخدمه علشان ننشئ منه كائنات (Objects) ليها نفس الخصائص والدوال.  
بتشبه فكرة الـ **Constructor Function** بس بشكل حديث ومنظم أكتر.

---

## ✍️ 2. طريقتين لكتابة الكلاس:

### ✅ Class Declaration:

```js
class Person {
	constructor(name) {
		this.name = name;
	}

	sayHi() {
		console.log(`Hi, I'm ${this.name}`);
	}
}
````

### ✅ Class Expression:

```js
const Person = class {
	constructor(name) {
		this.name = name;
	}

	sayHi() {
		console.log(`Hi, I'm ${this.name}`);
	}
};
```

---

## 🛠️ 3. الـ Constructor

- هو دالة خاصة بتشتغل أول ما تعمل كائن من الكلاس.
- بنستخدمه علشان ندي قيم أولية للخصائص (properties).

```js
class Car {
	constructor(brand) {
		this.brand = brand;
	}
}
```

---

## 🧪 4. ممكن تضيف Methods جوا الكلاس

```js
class Animal {
	constructor(type) {
		this.type = type;
	}
	sound() {
		console.log(`The ${this.type} makes a sound`);
	}
}
```

> كل دالة بنكتبها داخل الكلاس بتروح تلقائيًا على `Animal.prototype`

---

## ⚠️ 6. حاجات مهمة لازم تبقى عارفها:

| ❗ المفهوم               | 🔍 التوضيح                                                                                   |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| **Hoisting**            | الكلاسات **مش بتتعملها Hoisting**، يعني لازم تعرفها قبل ما تستخدمها.                         |
| **Strict Mode**         | الكلاسات بتشتغل دايمًا في وضع strict تلقائيًا.                                               |
| **First Class Citizen** | يعني تقدر تخزن الكلاس في متغير، تبعتها كـ argument، ترجعها من دالة... زيها زي أي قيمة تانية. |
| **Behind the scenes**   | الكلاس في الآخر بيشتغل بنفس نظام الـ `prototype`، بس الشكل الجديد منظم أكتر.                 |
| **مش دوال داخل object** | لما تكتب دالة داخل الكلاس، هي مش method على الكائن نفسه، لكن بتتحط في الـ prototype.         |

---

## 🧠 مثال يجمع كل حاجة:

```js
class Student {
	constructor(name, age) {
		this.name = name;
		this.age = age;
	}

	introduce() {
		console.log(`Hi, I'm ${this.name}, I'm ${this.age} years old.`);
	}
}

const ali = new Student("Ali", 22);
ali.introduce(); // Hi, I'm Ali, I'm 22 years old.
```

- ابحث عن `extend` و`super` ان شاء الله هشرحهم قدام ولاكن عاوزك تبحث عنهم وتاخد فكره عنهم من دلوقت.
---

## 🧩 الخلاصة:
- الكلاسات هي مجرد Syntax حديث للـ Prototype-based inheritance.
- بتخلينا نكتب الكود بشكل منظم وسهل.
- وبتشتغل زي الـ Constructor Function بس بشكل أوضح.

لو فهمت الكلاسات، يلا بينا  ندخل علي الي بعدو.