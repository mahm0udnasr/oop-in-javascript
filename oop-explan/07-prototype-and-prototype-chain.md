# 🧬 Prototype و Prototype Chain في JavaScript

## 📌 أولًا: يعني إيه Prototype؟

في JavaScript، كل كائن (Object) بيتبنى على كائن تاني.  
الكائن اللي بيتبني عليه ده بنسميه **Prototype**، وهو ببساطة كائن تاني JavaScript بيرجع له لما ميلاقيش خاصية (Property) أو دالة (Method) في الكائن الأصلي.

---

## 🎯 مثال عملي على الـ Prototype:

```js
const person = {
	speak() {
		console.log("Hello!");
	}
};

const student = Object.create(person);
student.name = "Mahmoud";

student.speak(); // Hello!
````

### ✨ شرح:

- كائن الـ `student` مش عنده دالة `speak`، لكن لما استدعيناها...
- راح JavaScript يدور عليها في **Prototype** بتاع `student` وهو `person`.

---

## 🔗 يعني إيه Prototype Chain؟

هي سلسلة (Chain) من الكائنات كل واحد بيشاور على الـ Prototype اللي قبله.  
الـ JavaScript لما بيدوّر على خاصية أو دالة، بيمشي في السلسلة دي لحد ما يلاقي الحاجة أو يوصل للآخر.
### 🔚 نهاية السلسلة:

آخر حاجة في السلسلة هي: `Object.prototype`  
ولو ملقاش الخاصية في أي مرحلة، بيرجع `undefined`.

---

## 📌 مثال يوضح الـ Prototype Chain:

```js
const human = {
	talk() {
		console.log("I can talk!");
	}
};

const developer = Object.create(human);
developer.code = function() {
	console.log("I write code.");
};

const frontEndDev = Object.create(developer);
frontEndDev.design = function() {
	console.log("I design interfaces.");
};

frontEndDev.talk();   // from human
frontEndDev.code();   // from developer
frontEndDev.design(); // from frontEndDev
```

### 🔍 السلسلة هنا:

```
frontEndDev 
   ⬇️
developer 
   ⬇️
human 
   ⬇️
Object.prototype
   ⬇️
null (نهاية السلسلة)
```

> الـ JavaScript بيمشي السلسلة دي واحدة واحدة لحد ما يلاقي اللي بيدوّر عليه.

---

## 🧪 ازاي تشوف الـ Prototype بتاع أي Object؟

```js
console.log(Object.getPrototypeOf(frontEndDev)); // 👉 developer
```

أو

```js
console.log(frontEndDev.__proto__); // مش افضل شئ مع ES6
```

---

## 🏗️ إزاي Prototype بيساعد في Inheritance؟

الـ Prototype هو الأساس اللي JavaScript بيستخدمه في عمل **Inheritance**.
بدل ما نكرر نفس الدوال في كل كائن، نقدر نحطهم في Prototype واحد، وكل الكائنات التانية تورث منهم.

---

## ⚠️ فرق مهم جدًا:

```js
function Person(name) {
	this.name = name;
}

Person.prototype.sayHi = function() {
	console.log(`Hi, I'm ${this.name}`);
};

const mahmoud = new Person("Mahmoud");

mahmoud.sayHi(); // Hi, I'm Mahmoud
```

> هنا `sayHi` مش جوه الكائن نفسه، لكن في **Prototype** بتاعه، وكل الكائنات اللي بتتعمل بـ `new Person()` هتورث الدالة دي.

---

## 🧠 الخلاصة:

|مفهوم|شرح بسيط|
|---|---|
|Prototype|كائن تاني JavaScript بيرجع له لما مبيلاقيش خاصية في الكائن الحالي.|
|Prototype Chain|سلسلة من الكائنات بيرجع لها JavaScript لحد ما يلاقي الخاصية أو يرجع undefined.|
|Inheritance|نظام الوراثة مبني على الـ Prototype، بدل تكرار الكود.|

---

**وبكده نكون فهمنا واحدة من أهم أفكار JavaScript: الوراثة من خلال Prototype وازاي بيشتغل النظام ده كله من ورا الكواليس 🔍🔥.**

يلا بينا نخش على اللي بعده ونتعمق أكتر 💻.