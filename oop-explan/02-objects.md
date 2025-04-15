## Creating Objects

في JavaScript، الـ object هو حجر الأساس، أي حاجة تقريباً بتتعامل معاها في JavaScript بتبقى object وده بيخلي التعامل معاه مرن جدًا.

### طيب يعني إيه object؟
هو ببساطة كيان (entity) بيجمع بيانات (properties) وسلوكيات (functions أو methods) في مكان واحد.

يعني مثلاً، لو عندك شخص، ممكن تمثله كـ object فيه اسمه وعنوانه، وكمان ممكن يكون ليه سلوك زي إنه يعرف يعرف نفسه.

### مثال عملي:

```js
const person = {
	name: "Mahmoud",
	address: {
		1: "Tanta",
		2: "Egypt"
	},
	getInfo: function() {
		console.log(`Hello there, I'm ${this.name} from ${this.address[1]}, ${this.address[2]}`);
	}
}
person.getInfo();
```

### شرح المثال:

- الـ `person`: ده اسم الـ object.
- الـ `name`: خاصية (property) بتخزن الاسم.
- الـ `address`: خاصية تانية بس جواها object تاني (يعني nested object).
- الـ `getInfo`: دي دالة (method) بتستخدم `this` علشان تجيب البيانات من نفس الـ object.

#### يعني إيه `this` هنا؟
الـ `this` بتشير للـ object الحالي اللي بيستدعي الدالة. فهنا `this.name` هترجع `"Mahmoud"` لأن `this` بتشير لـ `person` وان شاء الله هتلاقي ليها شرح بالتفصيل هنا [this keyword](09-this-keyword.md).

---

### 💡 ملحوظة:
أنت ممكن تضيف خصائص أو دوال لأي object حتى بعد ما تنشئ الكائن، ودي مرونة قوية في JavaScript هنتكلم عنها أكتر قدام.

---

### 👀 ملخص:

- تقدر تعمل object باستخدام الأقواس `{}`.
- كل خاصية بتكون عبارة عن زوج (key: value).
- تقدر تضيف دوال جوا الـ object علشان تمثل بيها السلوك.
- الـ `this` بتساعدك تتعامل مع نفس الـ object وانت جوا الدالة.

---

⏭️ الدرس الجاي: [Factory Functions](03-factory-functions.md) – وهنشوف فيه إزاي نعمل Object باستخدام دالة ترجع Object جديد كل مرة.
