# ⚙️ Static Methods in JavaScript

---

## 📌 يعني إيه Static Method؟

دي ميثود (دالة) بتتكتب جوا الكلاس، بس مش بتتربط بأي "instance" من الكلاس، يعني مش بتشتغل على كائن معين.  
بنستخدم الكلمة المفتاحية `static` قبل اسم الميثود.

---

## 🤔 بستخدمها ليه؟

- لما تحب تكتب وظيفة أو دالة لها علاقة بالكلاس نفسه، مش بالكائن اللي بيتعمل منه.
- غالبًا بتكون أدوات مساعدة أو utility methods.

---

## 🛠️ إزاي بكتبها؟

```js
class MathOperations {
	static add(x, y) {
		return x + y;
	}

	static multiply(x, y) {
		return x * y;
	}
}
````

---

## ✅ إزاي أستخدمها؟

مش بتحتاج تعمل `new` علشان تستخدمها، بتستخدمها على الكلاس نفسه:

```js
console.log(MathOperations.add(5, 3));       // 8
console.log(MathOperations.multiply(4, 2));  // 8
```

---

## ❌ إيه اللي مينفعش تعمله؟

```js
const op = new MathOperations();
console.log(op.add(5, 3)); // ❌ Error: op.add is not a function
```

الميثود static فـ مش متاحة على الـ instance.

---

## 🧠 إمتى تستخدم static؟

- لو الميثود مش بتحتاج تتعامل مع بيانات الكائن (يعني ملهاش علاقة بـ `this` أو بـ `constructor`).
- لو بتعمل عمليات عامة زي: تحويلات، حسابات، تنسيقات... إلخ.
- لو بتبني دالة بتساعد في إنشاء كائنات (factory method مثلًا).
---

## 🧪 مثال عملي بسيط

```js
class User {
	constructor(name) {
		this.name = name;
	}
	static greetEveryone() {
		console.log("Welcome, dear users!");
	}
	introduce() {
		console.log(`Hi, I'm ${this.name}`);
	}
}

const user1 = new User("Mahmoud");

User.greetEveryone(); // ✅ Welcome, dear users!
user1.introduce();    // ✅ Hi, I'm Mahmoud

// user1.greetEveryone(); // ❌ Error: user1.greetEveryone is not a function
```

---

> كده عرفنا يعني إيه Static Methods وإزاي نستخدمها!  
> يلا بينا نكمل الدروس الجاية.
