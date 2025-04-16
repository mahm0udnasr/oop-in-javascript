# 🔍 Understanding `this` in JavaScript

الـ `this` في JavaScript من أكتر الحاجات اللي بتتلغبط فيها الناس، علشان معناها بيتغير على حسب السياق اللي الكود بيتنفذ فيه.

في الملف ده هنشرح بالتفصيل:  
- يعني إيه `this`؟  
- إمتى بتتغير؟  
- إزاي نستخدمها؟  
- أمثلة توضيحية لكل حالة.

---

## 📌 1. يعني إيه `this`؟

الـ `this` هي **كلمة مفتاحية keyword** بتشير للكائن (object) اللي بينفذ الكود في اللحظة دي.
يعني:
- في بعض الحالات `this` بتشير لـ `window`
- وفي حالات تانية بتشير للكائن اللي بيحتوي على الفنكشن
- وفي حالات بتبقى undefined

---

## 🧪 2. `this` في Global Scope

```js
console.log(this); // في المتصفح هتطبع window
````

- لو أنت في أعلى مستوى (مش جوا أي فنكشن أو كلاس)، `this` هتشاور على `window` في المتصفح، أو `global` في Node.js
    

---

## 📦 3. `this` جوا Object Method

```js
const person = {
	name: "Mahmoud",
	sayHi: function () {
		console.log(`Hi, I'm ${this.name}`);
	}
};

person.sayHi(); // Hi, I'm Mahmoud
```

- هنا `this` بتشاور على الكائن `person`، لأنها جوا ميثود (method).
    

---

## ⚠️ 4. `this` جوا Regular Function

```js
function show() {
	console.log(this);
}

show(); // في المتصفح => window (في non-strict mode)
// في strict mode => undefined
```

> في الفنكشن العادية (مش جوا object)، `this` بتشير لـ `window` أو `undefined` لو كنت شغال بـ "strict mode"

---

## 🧰 5. `this` مع Arrow Function

```js
const person = {
	name: "Ahmed",
	sayHi: () => {
		console.log(`Hi, I'm ${this.name}`);
	}
};

person.sayHi(); // Hi, I'm undefined
```

> الـ Arrow Function **مبتعملش bind للـ `this`**  
> يعني بتاخد قيمة `this` من الـ scope الخارجي.

لو محتاج تستخدم `this` جوا method، متستخدمش arrow function.

---

## 🧠 6. `this` في Constructor Function

```js
function Person(name) {
	this.name = name;
	this.sayHi = function () {
		console.log(`Hi, I'm ${this.name}`);
	};
}

const ali = new Person("Ali");
ali.sayHi(); // Hi, I'm Ali
```

> لما تستخدم `new`، `this` بتشير للكائن الجديد اللي اتعمل من الفنكشن.

---

## 🏗️ 7. `this` في Classes

```js
class Animal {
	constructor(type) {
		this.type = type;
	}

	speak() {
		console.log(`I'm a ${this.type}`);
	}
}

const cat = new Animal("Cat");
cat.speak(); // I'm a Cat
```

> بالظبط زي الـ constructor function، `this` هنا بتشاور على الكائن الجديد اللي اتعمل من الكلاس.

---

## 🔁 8. ملخص سريع بقى 💡

|السياق|`this` بتشاور على إيه؟|
|---|---|
|Global Scope|`window` (في المتصفح) أو `global` في Node|
|Object Method|الكائن اللي استدعى الفنكشن|
|Regular Function|`window` أو `undefined` في strict mode|
|Arrow Function|بتاخد `this` من الـ scope اللي فوقها|
|Constructor Function|الكائن الجديد اللي بيتعمل بـ `new`|
|Class Method|الكائن الجديد اللي بيتعمل من الكلاس|

---

## 🧩 الخلاصة:

- الـ `this` مش ثابت، بيتغير حسب إنت فين في الكود.
- الـ Arrow Function مبتاخدش `this` خاص بيها.
- افهم السياق اللي الفنكشن بتتنفذ فيه علشان تحدد `this`.