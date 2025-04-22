# 🔐 Private Properties في JavaScript

## يعني إيه Private Properties؟
- هي **خصائص (Properties)** في الكلاس (Class) أو الكائن (Object) بتكون **مخفية ومش ممكن الوصول ليها من برّا الكلاس**.
- الهدف منها هو **حماية البيانات** ومنع التعديل عليها بطريقة غلط.

---
## 📌 ليه نستخدم Private Properties؟
- علشان **نخبي التفاصيل الداخلية** ونمنع أي حد يبوّظ الكائن.
- بتساعدنا نطبق مبدأ **Encapsulation (الكبسلة)** في البرمجة الكائنية.
- بنقلل الـ Bugs اللي بتحصل بسبب التلاعب في الخصائص من أماكن مش المفروض توصل لها.

---
## ✍️ إزاي نكتب Private Properties؟

### ✅ باستخدام علامة `#`

```js
class Person {
  #ssn; // Private property

  constructor(name, ssn) {
    this.name = name;
    this.#ssn = ssn;
  }

  getSSN() {
    return this.#ssn;
  }
}

const p = new Person("Mahmoud", "123-45-6789");

console.log(p.name);       // ✅ Mahmoud
console.log(p.getSSN());   // ✅ 123-45-6789
console.log(p.#ssn);       // ❌ Error: Private field '#ssn' must be declared in an enclosing class
````

> 💡 أي خاصية بتبدأ بعلامة `#` تبقى private ومينفعش تتشاف أو تتعدل من برّا الكلاس.

---

## 🧠 ملاحظات مهمة

- الـ **Private properties بتشتغل بس جوه الكلاسات.**
- **لازم تستخدم `#` في كل الأماكن اللي فيها الخاصية سواء في التعريف أو الاستخدام.**
- بتظهر Error صريح لو حاولت توصل ليها من برّا.

---

## ❓طيب لو عايز أخلي الناس تقرأ القيمة بس؟

تقدر تعمل Getter:

```js
class BankAccount {
  #balance;

  constructor(balance) {
    this.#balance = balance;
  }

  get balance() {
    return this.#balance;
  }
}

const account = new BankAccount(1000);
console.log(account.balance); // ✅ 1000
```

> ✅ كده سمحت للقراية بس بدون تعديل.

---

## ❓ولو عايز أسمح بتعديل تحت شروط معينة؟

استخدم Setter:

```js
class BankAccount {
  #balance;

  constructor(balance) {
    this.#balance = balance;
  }

  get balance() {
    return this.#balance;
  }

  set balance(value) {
    if (value < 0) {
      console.log("❌ رصيد غير صالح");
      return;
    }
    this.#balance = value;
  }
}

const account = new BankAccount(1000);
account.balance = -200;  // ❌ رصيد غير صالح
account.balance = 2000;  // ✅
console.log(account.balance); // ✅ 2000
```

---

## ⚠️ خلي بالك:

- الـ Private Properties مش زي الـ Underscore `_prop` اللي كنا بنستخدمها زمان، دي فعليًا **مش آمنة**، مجرد Convention.
- `#` هو النظام الرسمي للحماية فعليًا في JavaScript.

---

🚀 الحمدلله اولًا ثم مبروك خلصنا اخيرًا الـ OOP اتمني تكون استمتعت ومملتش من الشرح ولو في اي تقصير فهو مني ومن الشيطان وان اصبت فمن الله-عز وجل-  لو عندك اي فكره او تعديل معين ممكن تعمل fork وتبعت pull request وهراجعو ان شاء الله.. لو عندك مشكله معينه ممكن تتواصل معايا من خلال تيليجرام `@mahm0udnasr` اما من خلال انك تفتح issues, والسلام عليكم.