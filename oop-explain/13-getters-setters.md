# 🧠 Getters & Setters in JavaScript

## يعني إيه Getters و Setters؟
- هما ببساطة **طرق بتتحط جوه الكائن (object)** علشان تقدر **تقرأ أو تكتب على البيانات** بتاعته بطريقة منظمة.
- بدل ما توصّل مباشرة للـ property وتعدل فيها، بتستخدم **getter** علشان تقرا، و**setter** علشان تعدّل.

---
## 📌 ليه نستخدمهم؟
- **تنظيم البيانات** والتحكم فيها.
- **إخفاء التفاصيل** الداخلية (Abstraction).
- **التحقق من صحة القيم** قبل ما تتحط.
- **استخدام خواص محسوبة (computed)** بدل من تخزين بيانات مباشرة.

---

## ✍️ إزاي نكتب Getter و Setter؟

```js
let person = {
  firstName: "Mahmoud",
  lastName: "Nasr",

  // Getter
  get fullName() {
    return `${this.firstName} ${this.lastName}`;
  },

  // Setter
  set fullName(value) {
    const parts = value.split(" ");
    this.firstName = parts[0];
    this.lastName = parts[1];
  }
};

console.log(person.fullName); // Mahmoud Nasr

person.fullName = "Ahmed Salah";

console.log(person.firstName); // Ahmed
console.log(person.lastName);  // Salah
````

> ✅ خلي بالك: لما تستخدم `get` و `set` مفيش داعي تناديهم بكأنهم دوال (من غير أقواس).

---

## 🧪 إزاي نستخدمهم في التحقق من البيانات؟

```js
let user = {
  ageValue: 0,

  get age() {
    return this.ageValue;
  },

  set age(value) {
    if (value < 0) {
      console.log("السن لا يمكن يكون أقل من 0");
      return;
    }
    this.ageValue = value;
  }
};

user.age = -5; // ❌ السن لا يمكن يكون أقل من 0
user.age = 25;

console.log(user.age); // ✅ 25
```

---

## 🕹️ إمتى أستخدم الـ Getters و Setters؟

- لما تحب **تخلي فيه تحكم** على الوصول للقيم.
- لما تحب تضيف **تحقق أو معالجة** بسيطة قبل استخدام البيانات.
- لو عندك **خاصية بتحسب قيمتها بناءً على خواص تانية**.
- لو بتشتغل على **كائن كبير أو data model معقد**.

---

## 🎯 خليك فاكر:

- الـ Getters و Setters بيخلوك تتحكم في البيانات بدون ما تبوظ التركيب الداخلي للكائن.
- أداة قوية جدًا لو بتكتب كود قابل للتوسعة أو بتعمل data models.

---

🚀 يلا بينا نكمل على الدرس اللي بعده 🔥