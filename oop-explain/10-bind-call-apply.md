# 🔗 bind, call, apply في JavaScript

التلاتة دول بيستخدموا علشان تتحكم في `this` داخل الفنكشن، وخصوصًا لو هتنفذ الفنكشن في وقت أو مكان مختلف.

---

## 🧠 أولًا: الفرق بينهم بسرعة ⚡

| الطريقة     | بتنادي الفنكشن؟ | بتغير `this`؟ | بتقبل بارامترات؟        |
|-------------|------------------|----------------|---------------------------|
| `bind`      | ❌ (بترجع نسخة)  | ✅              | ✅ (كبارامترات عادية)     |
| `call`      | ✅                | ✅              | ✅ (كبارامترات عادية)     |
| `apply`     | ✅                | ✅              | ✅ (في Array)              |

---

## 🧪 مثال ثابت هنشتغل عليه

```js
const person = {
	name: "Mahmoud",
	sayHello: function(age, job) {
		console.log(`I'm ${this.name}, I'm ${age} years old and I'm a ${job}`);
	}
};

const otherPerson = {
	name: "Ali"
};
````

---

## 🔗 1. `bind`

بترجع نسخة جديدة من الفنكشن بس بـ `this` مختلف، ومش بتنفذها على طول.

```js
const sayHelloAli = person.sayHello.bind(otherPerson, 25, "Developer");
sayHelloAli(); // I'm Ali, I'm 25 years old and I'm a Developer
```

✅ Use case:

- لما تحب تمرر الفنكشن لمكان تاني وتنفذها بعدين، لكن عاوز تثبت `this`.
    

---

## ☎️ 2. `call`

بتنفذ الفنكشن فورًا، وتغير `this` وتبعت البارامترات **عادي**.

```js
person.sayHello.call(otherPerson, 30, "Designer");
// I'm Ali, I'm 30 years old and I'm a Designer
```

✅ Use case:

- لما تحب تنفذ الفنكشن فورًا بس بـ `this` مختلف.
    

---

## 📞 3. `apply`

نفس فكرة `call`، بس البارامترات بتتبعت على شكل Array.

```js
person.sayHello.apply(otherPerson, [35, "Engineer"]);
// I'm Ali, I'm 35 years old and I'm an Engineer
```

✅ Use case:

- لو معاك الداتا في Array وعاوز تبعتها كـ arguments.
    

---

## 🎯 ملخص سريع بقى

|الطريقة|إمتى تستخدمها؟|
|---|---|
|`bind`|لما تحب تخزن الفنكشن وتنفذها بعدين بـ `this` مختلف|
|`call`|لما تحب تنفذها فورًا بـ `this` وبارامترات عادية|
|`apply`|لما تحب تنفذها فورًا بـ `this` وبارامترات في Array|

---

## 🧩 الخلاصة :

- بتساعدك تكتب كود reusable أكتر.
- بتتحكم في `this` لو بتنادي الفنكشن من مكان تاني.
- بتفيد جدًا في الأحداث (events) أو الكولباك (callback functions).