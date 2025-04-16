# Functions are Objects in JavaScript

## يعني إيه الفنكشن في جافاسكريبت تعتبر Object؟

- في JavaScript، أي حاجة تقريبًا تعتبر Object، والفنكشن مش استثناء!
- الفنكشن في JavaScript مش بس كود بينفذ حاجة، هي كمان **(Object)** يقدر يكون ليه خصائص (Properties) ودوال (Methods).
- وده معناه إنك تقدر تتعامل مع الفنكشن زي ما بتتعامل مع أي Object تاني في اللغة.

---

## ✅ إثبات إن الفنكشن Object

```js
function sayHello() {
	console.log("Hello, world!");
}

console.log(typeof sayHello); // function
console.log(sayHello instanceof Object); // true
```

### شرح:

- `typeof sayHello`
	بيرجع `"function"`، لكن:
- `sayHello instanceof Object`
	بيرجع `true`!  
    يعني الفنكشن في الأصل كائن من نوع Object، لكن ليه نوع خاص اسمه `function`.
    

---

## 🧠 الفنكشن ممكن يكون ليها خصائص

```js
function greet(name) {
	console.log(`Hello, ${name}`);
}

greet.language = "English";
console.log(greet.language); // English
```

### شرح:

- هنا أضفنا خاصية `language` على الفنكشن `greet`.
    
- وده بيأكد إن الفنكشن مش مجرد كود بينفذ، ده كائن تقدر تضيف عليه بيانات.
    

---

## 🛠 للفنكشن Methods خاصة بيها زي bind, call, apply

```js
function intro(age) {
	console.log(`${this.name} is ${age} years old`);
}

const user = { name: "Mahmoud" };
intro.call(user, 20); // Mahmoud is 20 years old
```

### شرح:

- الـ `call` دي واحدة من الـ Methods اللي كل الفنكشنز بتورثها لأنها كائنات.
    
- تقدر تغير الـ `this` جوه الفنكشن باستخدام `call`, `apply`, أو `bind`.
    

---

## 🧪 الفنكشن ممكن تتخزن في متغير، وتتبع في Array، وتتبع في Object

```js
const add = (a, b) => a + b;

const myObject = {
	doSomething: add
};

const myArray = [add, console.log];

console.log(myObject.doSomething(2, 3)); // 5
myArray[1]("Functions are flexible!");   // Functions are flexible!
```

### شرح:

- الفنكشن زي أي كائن تاني، تقدر تخزنها في متغير، أو Array، أو حتى جوه Object.
    
- ده بيخلي JavaScript لغة ديناميكية جدًا ومناسبة للـ Functional Programming.
    

---

## 🧑‍🏫 الخلاصة:

|المعلومة|التوضيح|
|---|---|
|الفنكشن نوع خاص من الكائنات|بتقدر تضيف عليها خصائص وتستخدم دوال مدمجة فيها|
|ليها Methods زي call/bind/apply|وده بيخليك تتحكم في الـ `this` بمرونة|
|ممكن تتعامل معاها كـ بيانات|تحطها في متغير، Array، أو Object|
|ده بيخلي JavaScript مرنة جدًا|وتخليك تكتب كود نظيف وقابل لإعادة الاستخدام|

---

**ودي كانت نظرة شاملة عن إن الفنكشن في JavaScript في الحقيقة كائنات تقدر تتعامل معاها بمرونة كبيرة، وده جزء أساسي من قوة اللغة, يلا بينا نكمل الدروس.**