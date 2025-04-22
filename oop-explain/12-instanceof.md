# 🧬 `instanceof` في JavaScript

---

## 📌 يعني إيه `instanceof`؟

الكلمة المفتاحية `instanceof` بتستخدم علشان نعرف إذا كان كائن (object) معمول من كلاس أو فانكشن معينة (Constructor Function).

---

## 🤔 إمتى بستخدمها؟

لو عايز تتأكد إن object معين هو نسخة (instance) من كلاس أو constructor معين.

---

## ✅ الشكل العام

```js
object instanceof Constructor
````

بيرجع `true` لو `object` معمول باستخدام `Constructor`، غير كده بيرجع `false`.

---

## 🧪 مثال بسيط:

```js
class Person {
	constructor(name) {
		this.name = name;
	}
}

const person1 = new Person("Mahmoud");

console.log(person1 instanceof Person); // ✅ true
console.log(person1 instanceof Object); // ✅ true (لأن كل الكائنات تورث من Object)
```

---

## 🔍 مثال مع فانكشن Constructor

```js
function Animal(type) {
	this.type = type;
}

const cat = new Animal("cat");

console.log(cat instanceof Animal); // ✅ true
console.log(cat instanceof Object); // ✅ true
```

---

## ⛔ لو الكائن مش معمول من ال constructor

```js
const randomObj = {};

console.log(randomObj instanceof Animal); // ❌ false
```

---

## 🧠 طيب إزاي بيشتغل تحت الكواليس؟

الـ `instanceof` بيشيك على الـ **Prototype Chain**  
يعني بيشوف هل الـ prototype بتاع الـ constructor موجود في سلسلة البروتوتايب بتاعة الـ object.

---

## 🔄 مثال يوضح الكلام ده:

```js
function Car(model) {
	this.model = model;
}

const myCar = new Car("BMW");

console.log(Object.getPrototypeOf(myCar) === Car.prototype); // ✅ true
console.log(myCar instanceof Car); // ✅ true
```

---

## 💡 نستخدم `instanceof` ليه؟

- للتأكد من نوع الكائن قبل تنفيذ حاجة معينة.
- مفيدة في الـ Type Checking في اللوجيك المعقد.
- بتفيدك لو بتتعامل مع وراثة أو كائنات جاية من كلاس تاني وعايز تتأكد من نوعها.

---

## ⚠️ ملاحظة مهمة:

لو الكائن جه من **iframe** أو بيئة تانية (زي Window تانية في المتصفح)، `instanceof` ممكن ترجع نتيجة خاطئة بسبب اختلاف الـ prototype chain.

---

## 🧪 مثال advanced شوية:

```js
class Shape {}
class Rectangle extends Shape {}
class Circle extends Shape {}

const rect = new Rectangle();
const circ = new Circle();

console.log(rect instanceof Rectangle); // ✅ true
console.log(rect instanceof Shape);     // ✅ true
console.log(circ instanceof Circle);    // ✅ true
console.log(circ instanceof Shape);     // ✅ true
console.log(circ instanceof Rectangle); // ❌ false
```

---

> ✅ كده انت فهمت `instanceof` صح وبالتفصيل  
> يلا نخش عاللي بعده 🔥  