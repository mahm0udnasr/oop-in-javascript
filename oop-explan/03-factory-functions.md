# 🏭 Factory Functions

## يعني إيه Factory Function؟ 🤔

- الـ Factory Function هي دالة (Function) بترجع Object جديد كل مرة بتستدعيها.
- يعني بدل ما تكتب الكائن (object) بإيدك كل مرة، لأ، انت بتعمل دالة تخلقلك object جاهز بالقيم اللي انت تبعتها.

---

## ✅ ليه نستخدم Factory Function؟

- **تكرار أقل للكود**: بدل ما تكتب نفس الكود كل مرة.
- **سهولة التعديل**: لو عايز تعدل على شكل الـ object بعدين، بتعدل في مكان واحد بس (جوه الدالة).
- **مرونة أكتر**: تقدر تضيف دوال (methods) جوه الـ object بكل سهولة.

---

## 📦 مثال عملي:

```js
// Factory Function
function createPerson(name) {
	return {
		name,
		sayHello: function() {
			console.log(`Hello I'm ${this.name}`);
		}
	}
}

const personOne = createPerson("Mahmoud");
const personTwo = createPerson("Ahmed");
const personThree = createPerson("Ali");

personOne.sayHello();  // Hello I'm Mahmoud
personTwo.sayHello();  // Hello I'm Ahmed
personThree.sayHello(); // Hello I'm Ali
````

---
## 🧠 خد بالك:

- كل مرة بتستدعي `createPerson()`، الدالة دي بتبني object جديد مستقل تمامًا.
- الدالة بترجع Object literal، وممكن يكون فيه خصائص (properties) أو دوال (methods) أو nested objects كمان.

> الـ **Object Literal** يعني لما تكتب كائن (object) في جافاسكريبت بشكل مباشر كده بين `{}` من غير ما تعمل كلاس أو دالة

---

## 🧪 جربها بنفسك

حاول تعمل Factory Function تانية، وليكن مثلًا `createCar`، فيها `model` و`startEngine()` وتطبع رسالة.

---

**وبكده نكون فهمنا الـ Factory Functions واحدة واحدة 👏، ويلا بينا نكمل الدرس الجاي 🔥.**