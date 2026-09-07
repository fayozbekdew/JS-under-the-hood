# JavaScript — Full Interview Question Bank

> Jami 28 ta mavzu, 444 ta savol. Faqat savollar (javobsiz), og'zaki AI mock interview uchun moslashtirilgan — kod o'qib "output"ni taxmin qilish talab qilinadigan savollar chiqarib tashlangan; o'rniga tegishli mavzulardagi bo'shliqlar yopilgan.

## Mundarija

1. [JS Engine](#1-js-engine) — 15 savol
2. [Execution Context](#2-execution-context) — 10 savol
3. [Hoisting](#3-hoisting) — 8 savol
4. [Scope](#4-scope) — 14 savol
5. [Closures](#5-closures) — 14 savol
6. [Objects](#6-objects) — 14 savol
7. [Prototypal Inheritance](#7-prototypal-inheritance) — 18 savol
8. [ES6 Classes](#8-es6-classes) — 15 savol
9. [Functions — First-Class Citizens](#9-functions-first-class-citizens) — 20 savol
10. [this Keyword Mastery](#10-this-keyword-mastery) — 13 savol
11. [Event Loop](#11-event-loop) — 14 savol
12. [Promises](#12-promises) — 15 savol
13. [Async/Await](#13-async-await) — 17 savol
14. [Iterators va Generators](#14-iterators-va-generators) — 17 savol
15. [Modules](#15-modules) — 15 savol
16. [Memory Management](#16-memory-management) — 17 savol
17. [Type Coercion va Equality](#17-type-coercion-va-equality) — 20 savol
18. [DOM Manipulation](#18-dom-manipulation) — 20 savol
19. [Events](#19-events) — 19 savol
20. [Browser APIs](#20-browser-apis) — 23 savol
21. [Error Handling](#21-error-handling) — 17 savol
22. [Modern JavaScript (ES6+)](#22-modern-javascript-es6) — 18 savol
23. [Array Methods Mastery](#23-array-methods-mastery) — 15 savol
24. [Proxy va Reflect](#24-proxy-va-reflect) — 14 savol
25. [Design Patterns](#25-design-patterns) — 16 savol
26. [String Methods](#26-string-methods) — 15 savol
27. [Date va Intl API](#27-date-va-intl-api) — 16 savol
28. [ES2024+ va Kelgusi Standartlar](#28-es2024-va-kelgusi-standartlar) — 15 savol

---

## 1. JS Engine

**1. JavaScript Engine nima va u qanday ishlaydi? [Junior+]**

**2. JIT Compilation nima? Interpreter va Compiler'dan qanday farq qiladi? [Middle]**

**3. V8 Engine pipeline'ini bosqichma-bosqich tushuntiring [Senior]**

**4. AST (Abstract Syntax Tree) nima va qayerda ishlatiladi? [Junior+]**

**5. V8 dagi Hidden Classes nima va ular nima uchun kerak? [Middle+]**

**6. Inline Caching nima va Monomorphic, Polymorphic, Megamorphic farqi nima? [Senior]**

**7. Call Stack nima va JavaScript nima uchun single-threaded? [Junior+]**

**8. V8 da Deoptimization nima va qachon sodir bo'ladi? [Senior]**

**9. Stack va Heap farqi nima? Primitive va Reference type'lar qayerda saqlanadi? [Junior+]**

**10. Bu kodda performance muammo bor. Toping va tuzating [Middle+]**

```javascript
function processUsers(users) {
  const results = [];
  for (const user of users) {
    if (user.type === 'admin') {
      const adminUser = {};
      adminUser.role = 'admin';
      adminUser.name = user.name;
      adminUser.permissions = ['read', 'write', 'delete'];
      results.push(adminUser);
    } else {
      const regularUser = {};
      regularUser.name = user.name;
      regularUser.role = 'user';
      regularUser.permissions = ['read'];
      results.push(regularUser);
    }
  }
  return results;
}
```

**11. V8 uchun optimized bo'lgan `createPoint` factory function yozing [Middle+]**

**Savol:** `createPoint(x, y)` funksiyasi yozing — V8 Hidden Classes va Inline Caching uchun optimal bo'lsin.

**12. Lazy Parsing (Pre-parsing) nima va nima uchun kerak? [Senior]**

**13. Asosiy JavaScript engine'larni (V8, SpiderMonkey, JavaScriptCore) taqqoslang — komponentlari va farqlari nima? [Middle]**

**14. Recursive funksiya juda chuqur bo'lib ketsa nima uchun "Maximum call stack size exceeded" xatosi chiqadi? [Middle]**

**15. Scanner/Tokenizer va Parser'ning vazifasi nima? Ular AST bilan qanday bog'liq? [Junior+]**


## 2. Execution Context

**1. Execution Context nima va unda qanday komponentlar bor? [Junior+]**

**2. Execution Context necha xil bo'ladi? [Junior+]**

**3. Creation Phase va Execution Phase da nima sodir bo'ladi? [Middle]**

**4. Variable Environment va Lexical Environment farqi nima? [Middle+]**

**5. Environment Record turlari va farqlari nima? [Senior]**

**6. Global scope'da var bilan e'lon qilingan o'zgaruvchi let dan nima farq qiladi? [Middle]**

**7. Bu kodda xato bor. Toping va tuzating [Middle]**

```javascript
function getUserRole(userId) {
  if (userId === 1) {
    var role = "admin";
    var permissions = ["read", "write", "delete"];
  } else {
    var role = "user";
    var permissions = ["read"];
  }

  return { role, permissions };
}
```

**8. eval() nima uchun ishlatmaslik kerak? [Middle]**

**9. Execution Context Stack qanday ishlaydi — funksiya chaqirilganda va tugaganda unda nima o'zgaradi? [Middle]**

**10. Outer Environment Reference orqali Scope Chain qanday hosil bo'ladi? [Middle+]**


## 3. Hoisting

**1. Hoisting nima? [Junior+]**

**2. let va const hoist bo'ladimi? [Middle]**

**3. TDZ (Temporal Dead Zone) nima? [Middle]**

**4. Function declaration vs function expression hoisting farqi nima? [Junior+]**

**5. var vs let vs const farqlarini jadval bilan tushuntiring [Junior+]**

**6. Bu kodda xato bor. Toping va tuzating [Middle]**

```javascript
function getItems() {
  var items = [];

  for (var i = 0; i < 3; i++) {
    items.push(function() {
      return i;
    });
  }

  return items;
}

const fns = getItems();
console.log(fns[0]()); // kutilgan: 0
console.log(fns[1]()); // kutilgan: 1
console.log(fns[2]()); // kutilgan: 2
```

**7. Class hoisting boshqa deklaratsiyalardan (function, var) nima bilan farq qiladi — bunga TDZ qanday ta'sir qiladi? [Middle]**

**8. Function declaration va o'zgaruvchi (var) hoisting'i orasida ustuvorlik (priority) qanday belgilanadi? [Middle+]**


## 4. Scope

**1. Scope nima va JavaScript da qanday scope turlari mavjud? [Junior+]**

**2. Lexical scope nima va dynamic scope dan farqi? [Middle]**

**3. Scope chain nima va qanday ishlaydi? [Middle]**

**4. Variable shadowing nima? [Middle]**

```javascript
let count = 100;

function outer() {
  let count = 0;

  function increment() {
    let count = count + 1;
    return count;
  }

  return increment();
}

console.log(outer()); // ?
```

**5. `globalThis` nima va nima uchun kerak? [Junior+]**

**6. `var` ning block scope tanimasligini tushuntiring va bu qanday muammolarga olib keladi? [Junior+]**

**7. Strict mode nima va u scope'ga qanday ta'sir ko'rsatadi? [Middle]**

**8. Quyidagi kodda nima xato va qanday tuzatasiz? [Middle+]**

```javascript
function createHandlers(elements) {
  var handlers = [];

  for (var i = 0; i < elements.length; i++) {
    handlers.push(function () {
      console.log(`Element ${i}: ${elements[i]}`);
    });
  }

  return handlers;
}

const handlers = createHandlers(["a", "b", "c"]);
handlers[0](); // ?
handlers[1](); // ?
handlers[2](); // ?
```

**9. `let`, `const`, `var` ning scope farqlarini jadvali bilan tushuntiring [Junior+]**

**10. Scope chain va call stack farqi nima? [Senior]**

**11. Module scope nima va global scope dan farqi? [Middle]**

**12. Scope bilimingizni ishlatib, quyidagi muammoni hal qiling [Senior]**

**Savol:** `createPrivateCounter()` funksiyasini yozing. U `increment()`, `decrement()`, `getCount()`, `reset()` method'lariga ega object qaytarsin. `count` tashqaridan o'zgartirilishi mumkin bo'lmasin.

**13. `with` statement nima uchun taqiqlangan va u scope chain'ga qanday ta'sir ko'rsatadi? [Senior]**

**14. Variable Lookup — o'zgaruvchini qidirish jarayoni scope chain bo'ylab qanday amalga oshiriladi? [Middle]**


## 5. Closures

**1. Closure nima? [Junior+]**

**2. Bir xil scope'da yaratilgan ikkita funksiya (masalan getValue/setValue) bitta o'zgaruvchiga ta'sir qilganda, closure reference saqlaydimi yoki copy? Tushuntiring. [Middle]**

**3. Klassik loop + closure muammosini tushuntiring [Middle+]**

**4. Closure va memory haqida nima bilasiz? [Senior]**

**5. Closure yordamida private variable yarating [Middle]**

**Savol:** `createPerson(name, age)` funksiyasini yozing. `name` va `age` tashqaridan to'g'ridan-to'g'ri o'zgartirilishi mumkin bo'lmasin. Faqat `getName()`, `getAge()`, `setAge(newAge)` (validation bilan) method'lari bo'lsin.

**6. `memoize` funksiyasini implement qiling [Middle+]**

**7. Quyidagi kodda xato toping va tuzating [Middle+]**

```javascript
function setupClickHandlers() {
  const buttons = document.querySelectorAll(".btn");

  for (var i = 0; i < buttons.length; i++) {
    buttons[i].addEventListener("click", function() {
      alert("Button " + i + " clicked");
    });
  }
}
```

**8. `once()`, `debounce()`, `throttle()` — bularning closure bilan aloqasi nima? [Middle+]**

**9. Closure va this ning farqi nima? [Senior]**

**10. Stale closure nima? Real-world misolini ko'rsating [Senior]**

**11. Closure bilan module pattern implement qiling [Middle]**

**Savol:** IIFE + closure yordamida `TodoModule` yarating: `addTodo(text)`, `removeTodo(id)`, `getTodos()`, `getCount()`.

**12. V8 closure'ni qanday optimizatsiya qiladi? [Senior]**

**13. Closure bilan private method'larni qanday yaratasiz? Class `#private` dan farqi nima? [Senior]**

**14. Closure'lardan ko'p foydalanish performance va memory'ga qanday ta'sir qilishi mumkin? Qachon ehtiyot bo'lish kerak? [Middle+]**


## 6. Objects

**1. Object yaratishning qanday usullari bor? [Junior+]**

**2. Property descriptor nima? [Middle]**

**3. `Object.freeze`, `Object.seal`, `Object.preventExtensions` farqi nima? [Middle]**

**4. Shallow copy va deep copy farqi nima? Qanday usullar bor? [Middle]**

**5. `for...in` vs `Object.keys()` vs `Reflect.ownKeys()` farqi nima? [Middle]**

**6. `Object.hasOwn()` nima va `hasOwnProperty` dan farqi? [Junior+]**

**7. Getter va Setter nima? Qachon ishlatiladi? [Middle]**

**8. `deepClone` funksiyasini implement qiling [Senior]**

**9. `deepEqual` funksiyasini implement qiling [Senior]**

**10. `Object.groupBy()` nima va qanday ishlaydi? [Junior+]**

**11. `structuredClone` nima va JSON hack dan farqi? [Middle]**

**12. Optional chaining (`?.`) qanday ishlaydi va qachon ishlatiladi? [Junior+]**

**13. V8 Hidden Class nima va performance'ga qanday ta'sir qiladi? [Senior]**

**14. Computed property names va object shorthand syntax nima? Misol bilan tushuntiring [Junior+]**


## 7. Prototypal Inheritance

**1. `__proto__` va `prototype` farqi nima? [Junior+]**

**2. Prototype chain nima va qanday ishlaydi? [Junior+]**

**3. `new` keyword ichida nima sodir bo'ladi? Step-by-step tushuntiring. [Middle]**

**4. `Object.create(null)` nima va nima uchun ishlatiladi? [Middle]**

**5. Property shadowing nima? Quyidagi kodda nima sodir bo'ladi? [Middle]**

**Savol:**

```javascript
const parent = { count: 0 };
const child = Object.create(parent);

child.count++;

console.log(child.count);
console.log(parent.count);
console.log(Object.hasOwn(child, "count"));
```

**6. Bu kodda nima xato? Qanday tuzatish kerak? [Middle]**

**Savol:**

```javascript
function Team(name) {
  this.name = name;
}
Team.prototype.members = [];
Team.prototype.addMember = function(member) {
  this.members.push(member);
};

const alpha = new Team("Alpha");
const beta = new Team("Beta");

alpha.addMember("Ali");
console.log(beta.members);
```

**7. `instanceof` ni implement qiling [Middle+]**

**Savol:** `myInstanceof(obj, Constructor)` funksiyasini yozing.

**8. `new` keyword polyfill yozing [Senior]**

**Savol:** `myNew(Constructor, ...args)` funksiyasini yozing — `new` keyword'ning to'liq polyfill'i.

**9. Constructor inheritance qanday qilinadi? (ES5 usuli) [Middle+]**

**10. Prototype'da `writable: false` bo'lganda nima bo'ladi? [Senior]**

**Savol:**

```javascript
const parent = {};
Object.defineProperty(parent, "x", {
  value: 10,
  writable: false,
  configurable: true
});

const child = Object.create(parent);
child.x = 20;

console.log(child.x);
console.log(Object.hasOwn(child, "x"));
```

**11. `for...in`, `Object.keys`, `Object.getOwnPropertyNames` farqi nima? [Middle]**

**12. Prototype-based inheritance va class-based inheritance farqi nima? [Senior]**

**13. Prototype pollution nima va qanday himoya qilish? [Senior]**

**14. Tuzatish — Prototype inheritance noto'g'ri ishlayapti [Middle]**

**Savol:** Quyidagi kodda `Dog` `Animal` dan meros olishi kerak, lekin to'g'ri ishlamayapti. Xatolarni toping:

```javascript
function Animal(name) { this.name = name; }
Animal.prototype.speak = function() {
  return `${this.name} ovoz chiqaradi`;
};

function Dog(name, breed) {
  this.name = name;
  this.breed = breed;
}

Dog.prototype = Animal.prototype;

Dog.prototype.bark = function() {
  return `${this.name} vov-vov deydi`;
};

const dog = new Dog("Bobik", "Labrador");
const cat = new Animal("Mushuk");

console.log(cat.bark()); // Bu ishlamamasligi kerak edi!
```

**15. Tuzatish — Prototype method instance property bilan shadow bo'lib qolgan [Middle+]**

**Savol:** `getDiscount()` ba'zi hollarda noto'g'ri ishlayapti. Xatoni toping:

```javascript
function Product(name, price) {
  this.name = name;
  this.price = price;
  if (price > 100000) {
    this.getDiscount = function() {
      return this.price * 0.15;
    };
  }
}

Product.prototype.getDiscount = function() {
  return this.price * 0.05;
};

const laptop = new Product("Laptop", 500000);
console.log(laptop.getDiscount()); // 75000 (15%) ✅

laptop.price = 80000;
console.log(laptop.getDiscount()); // 12000 (15%) ❌ — 5% bo'lishi kerak!
```

**16. Mixin pattern prototype bilan qanday qilinadi? [Senior]**

**17. Prototype method va instance method farqi nima? [Middle+]**

**18. Symbol.hasInstance nima? `instanceof` operatorining xatti-harakatini qanday o'zgartirish mumkin? [Senior]**


## 8. ES6 Classes

**1. Class nima va prototype bilan qanday bog'liq? [Junior+]**

**2. Class va constructor function o'rtasidagi farqlar nima? [Middle]**

**3. `extends` va `super` qanday ishlaydi? [Middle]**

**4. Private fields (`#`) va underscore convention (`_`) farqi nima? [Middle]**

**5. Static method nima va qachon ishlatiladi? [Middle]**

**6. Class field'lar (public va arrow function) qanday ishlaydi? [Middle]**

**7. Bu kodda nima xato? [Middle]**

**Savol:**

```javascript
class Animal {
  constructor(name) { this.name = name; }
  speak() { return `${this.name} speaks`; }
}

class Dog extends Animal {
  constructor(name, breed) {
    this.breed = breed;
    super(name);
  }
}

const rex = new Dog("Rex", "Labrador");
```

**8. Getter va setter class'da qanday ishlaydi? [Middle]**

**9. Static initialization block nima? [Middle+]**

**10. Mixin pattern class'larda qanday qilinadi? [Senior]**

**11. Composition vs inheritance — qachon qaysi biri? [Senior]**

**12. `#private in obj` tekshiruvi nima? [Middle+]**

**13. Bu kodda nima xato? [Middle]**

**Savol:**

```javascript
class Logger {
  prefix = "[LOG]";

  log(message) {
    console.log(`${this.prefix} ${message}`);
  }
}

const logger = new Logger();
const log = logger.log;
log("test");
```

**14. Class'da `new.target` nima? [Senior]**

**15. Private static field va method nima? Instance private a'zolaridan farqi nima? [Middle+]**


## 9. Functions — First-Class Citizens

**1. Function Declaration, Function Expression va Arrow Function — farqlari nima? [Junior+]**

**2. First-class function nima degani? [Junior+]**

**3. IIFE nima? Nima uchun ishlatiladi? [Junior+]**

**4. Higher-Order Function (HOF) nima? Misol bering. [Junior+]**

**5. Callback nima? Callback hell nima? [Junior+]**

**6. Pure Function nima? Side Effect nima? [Middle]**

**7. `arguments` vs Rest Parameters — farqi nima? [Middle]**

**8. Default Parameters qanday ishlaydi? [Middle]**

**9. Currying nima? Universal `curry` funksiyasini implement qiling. [Middle+]**

**10. Partial Application nima? Currying dan farqi? [Middle+]**

**11. Function Composition nima? `pipe` va `compose` ni implement qiling. [Senior]**

**12. `debounce` funksiyasini implement qiling. [Middle+]**

**13. `throttle` funksiyasini implement qiling. [Middle+]**

**14. `memoize` funksiyasini implement qiling. [Middle+]**

**15. Quyidagi kodni tuzating (Fix the bug). [Middle]**

```javascript
// ❌ Bug: har chaqiruvda oldingi natijalar qo'shiladi
function addToList(item, list = []) {
  list.push(item);
  return list;
}

console.log(addToList("a")); // ["a"]
console.log(addToList("b")); // ["b"] — kutilgan, lekin...
// Python da xatolik bo'lardi (mutable default), JS da bu TO'G'RI ishlaydi!

// ❌ HAQIQIY muammo — bu usulda:
const defaultList = [];
function addToList2(item, list = defaultList) {
  list.push(item);
  return list;
}

console.log(addToList2("a")); // ["a"]
console.log(addToList2("b")); // ["a", "b"] — ❌ oldingi "a" ham bor!
```

**16. `pipe` funksiyasini yozing — har bir bosqichda log chiqarsin. [Senior]**

**17. Quyidagi kodni tuzating (Fix the bug). [Middle+]**

```javascript
// ❌ Bug: once funksiyasi to'g'ri ishlamayapti
function once(fn) {
  let called = false;
  return function(...args) {
    if (!called) {
      called = true;
      fn(...args);
    }
  };
}

const pay = once(function(amount) {
  console.log(`To'lov: ${amount} so'm`);
  return amount;
});

const result = pay(50000);
console.log(result); // undefined ❌ — kutilgan: 50000
pay(100000);         // chaqirilmadi ✅ — bu to'g'ri
```

**18. Funksiya object'ining `name` va `length` propertylari nima uchun kerak va qanday hisoblanadi? [Middle]**

**19. `arguments` object bilan nomlangan parametrlar orasidagi bog'lanish (linking) qanday ishlaydi va strict mode'da bu qanday o'zgaradi? [Middle+]**

**20. Default parametr yoki qiymat belgilashda `||` ishlatishning xavfi nima — 0, "", false kabi falsy qiymatlar yo'qolishi mumkinmi? [Middle]**


## 10. this Keyword Mastery

**1. `this` nima va qanday aniqlanadi? [Junior+]**

**2. `this` binding 4 ta qoidasi nima? (Priority tartibida) [Middle]**

**3. `call` vs `apply` vs `bind` farqi nima? [Middle]**

**4. Arrow function va `this` — nima farq? [Middle]**

**5. `this` yo'qotish muammosi va yechimi [Middle]**

**6. `Function.prototype.bind` polyfill yozing [Senior]**

**7. `this` turli kontekstlarda nima? [Middle]**

**8. Strict mode `this` ga qanday ta'sir qiladi? [Middle]**

**9. Bu kodda nima muammo bor va qanday tuzatasiz? [Middle]**

```javascript
class Timer {
  constructor() {
    this.seconds = 0;
  }
  start() {
    setInterval(function() {
      this.seconds++;
      console.log(this.seconds);
    }, 1000);
  }
}
new Timer().start(); // Nima bo'ladi?
```

**10. Method chaining va `this` [Middle]**

**11. `this` va Proxy [Senior]**

**12. globalThis nima? [Junior+]**

**13. `new` orqali chaqirilgan konstruktor funksiya ichida `return` qilinsa (object yoki primitive holatlarida) nima bo'ladi? [Middle+]**


## 11. Event Loop

**1. JavaScript nima uchun single-threaded? [Junior+]**

**2. Event Loop nima va qanday ishlaydi? [Middle]**

**3. Microtask va Macrotask farqi nima? [Middle]**

**4. setTimeout(fn, 0) nima uchun darhol bajarmaydi? [Middle]**

**5. Promise constructor sync ishlashini tushuntiring [Middle]**

**6. requestAnimationFrame Event Loop'da qayerda turadi? [Middle+]**

**7. Starvation nima va qanday oldini olish mumkin? [Middle+]**

**8. Node.js Event Loop browser'nikidan qanday farq qiladi? [Middle+]**

**9. UI blocking muammosini qanday hal qilasiz? [Middle+]**

**10. queueMicrotask() nima va qachon ishlatiladi? [Middle]**

**11. process.nextTick() va queueMicrotask() farqi nima? (Node.js) [Senior]**

**12. Quyidagi kodda nima xato va qanday tuzatasiz? [Middle+]**

**Savol:**

```javascript
// Foydalanuvchi "Load" tugmasini bosganda 50,000 ta yozuvni ko'rsatish
loadBtn.addEventListener("click", () => {
  const records = fetchRecordsSync(); // 50,000 ta yozuv

  records.forEach(record => {
    const row = document.createElement("tr");
    row.innerHTML = `<td>${record.name}</td><td>${record.email}</td>`;
    table.appendChild(row);
  });
});
```

**13. requestIdleCallback nima va requestAnimationFrame dan farqi? [Senior]**

**14. Brauzer runtime arxitekturasi — Call Stack, Web APIs, Callback Queue va Microtask Queue bir-biriga qanday bog'langan? [Middle]**


## 12. Promises

**1. Promise nima? [Junior+]**

**2. Promise constructor qanday ishlaydi? [Middle]**

**3. `.then()`, `.catch()`, `.finally()` farqi nima? [Middle]**

**4. Promise.all() va Promise.allSettled() farqi nima? [Middle]**

**5. Promise.race() va Promise.any() farqi nima? [Middle+]**

**6. Error propagation qanday ishlaydi? [Middle]**

**7. `Promise.all()` ni implement qiling [Middle+]**

**8. `Promise.allSettled()` ni implement qiling [Senior]**

**9. `sleep` funksiyasini yozing [Junior+]**

**10. Promise.withResolvers() nima? (ES2024) [Middle+]**

**11. Bu kodda nima xato? [Middle+]**

**Savol:**

```javascript
new Promise(async (resolve, reject) => {
  const data = await fetchData();
  resolve(data);
});
```

**12. Promise.race() ni implement qiling [Middle+]**

**13. Retry pattern yozing [Middle+]**

**14. Promise ichidan boshqa Promise (yoki thenable) qaytarilsa, bu microtask navbatiga qanday ta'sir qiladi? [Senior]**

**15. Promise bilan timeout pattern (masalan `Promise.race` yordamida) qanday implement qilinadi? [Middle+]**


## 13. Async/Await

**1. `async/await` nima? Promise bilan farqi nima? [Junior+]**

**2. Sequential vs Parallel — qachon qaysi biri? [Middle]**

**3. `forEach` ichida `await` ishlaydimi? [Middle+]**

**4. `return await` kerakmi? [Middle+]**

**5. Bu kodda nima xato? [Middle+]**

**Savol:**

```javascript
async function loadAllUsers(ids) {
  const users = [];
  for (const id of ids) {
    const user = await fetchUser(id);
    users.push(user);
  }
  return users;
}
```

**6. Async function vs Promise — qachon qaysi birini ishlatish kerak? [Middle]**

**7. `Promise.all` vs `Promise.allSettled` — qachon qaysi biri? [Middle]**

**8. Top-level await nima? Qayerda ishlaydi? [Middle]**

**9. `retry` funksiyasini exponential backoff bilan implement qiling [Middle+]**

**Savol:** Asinxron funksiyani xato bo'lganda qayta ishlatadigan `retry(fn, maxRetries, baseDelay)` yozing. Har safar kutish vaqti 2x oshsin.

**10. `AbortController` bilan request cancel qilish [Middle+]**

**11. Async constructor bo'ladimi? [Middle]**

**12. `for-await-of` nima? Qachon ishlatiladi? [Middle+]**

**13. `Promise.all` + `await` da bitta xato bo'lsa nima bo'ladi? [Middle]**

**14. Async/Await under the hood qanday ishlaydi? [Senior]**

**15. Concurrent limit implement qiling [Senior]**

**Savol:** `mapWithLimit(items, limit, fn)` — bir vaqtda max `limit` ta task parallel ishlashi kerak, natijalar tartibini saqlang.

**16. Async funksiya har doim Promise qaytarishini tushuntiring — funksiya ichida oddiy (sync) qiymat return qilinganda ham-chi? [Junior+]**

**17. Async funksiya ichida `try/catch` orqali xatolarni ushlashning eng keng tarqalgan usuli qanday ishlaydi? [Junior+]**


## 14. Iterators va Generators

**1. Iterable va Iterator farqi nima? [Junior+]**

**2. `for...of` va `for...in` farqi nima? [Junior+]**

**3. Generator nima? Oddiy funksiyadan farqi? [Middle]**

**4. `yield*` nima qiladi? [Middle]**

**5. Custom iterable ob'ekt qanday yaratiladi? [Middle]**

**6. Bu kodda nima xato? [Middle+]**

**Savol:**

```javascript
function* fetchAll(urls) {
  urls.forEach(async url => {
    const res = await fetch(url);
    yield await res.json();
  });
}
```

**7. Generator'ni qayta ishlatsa bo'ladimi? [Middle]**

**8. Lazy evaluation nima? Generator bilan qanday bog'liq? [Middle+]**

**9. `generator.return()` va `generator.throw()` nima qiladi? [Middle+]**

**10. Async generator nima? Qachon ishlatiladi? [Middle+]**

**11. Spread operator iterable bo'lmagan object bilan ishlaydimi? [Middle]**

**12. `for...of` da `return` qiymati nima uchun ko'rinmaydi? [Middle+]**

**13. Generator bilan infinite Fibonacci ketma-ketligini yozing [Middle]**

**14. Generator va async/await bog'liqligi nima? [Senior]**

**15. Iterator Helpers (ES2025) nima? [Senior]**

**16. `generator.next(value)` orqali generatorga tashqaridan qiymat yuborish (two-way communication) qanday ishlaydi? [Middle+]**

**17. JavaScript'da qaysi built-in object'lar iterable hisoblanadi (Array, String, Map, Set va h.k.)? Oddiy Object nega iterable emas? [Junior+]**


## 15. Modules

**1. CommonJS va ES Modules farqi nima? [Junior+]**

**2. `module.exports` va `exports` farqi nima? [Middle]**

**3. Live bindings nima? [Middle+]**

**4. Named export va Default export farqi nima? [Junior+]**

**5. `import()` dynamic import nima? Qachon ishlatiladi? [Middle]**

**6. Circular dependency nima? Qanday oldini olish mumkin? [Middle+]**

**7. Tree shaking nima? Nima uchun faqat ESM bilan ishlaydi? [Middle]**

**8. ESM da `require()` ishlatsa bo'ladimi? [Middle]**

**9. `import * as` va `import { }` farqi nima? [Middle]**

**10. Node.js da CJS va ESM ni qanday farqlaydi? [Middle+]**

**11. `import.meta` nima? [Middle+]**

**12. Re-export (barrel file) nima? Performance muammosi bormi? [Middle+]**

**13. ESM da top-level await ishlaydi, CJS da nima uchun ishlamaydi? [Middle+]**

**14. Module bundler nima? Webpack va Vite farqi? [Middle]**

**15. Module bundler dependency graph orqali qanday ishlaydi — barcha modullar qanday qilib bitta bundle faylga yig'iladi? [Middle]**


## 16. Memory Management

**1. Stack va Heap farqi nima? Qaysi ma'lumotlar qayerda saqlanadi? [Junior+]**

**2. Copy by value va copy by reference farqi nima? [Junior+]**

**3. Garbage Collection qanday ishlaydi? Mark-and-Sweep nima? [Middle]**

**4. Memory leak nima? Eng keng tarqalgan turlari qaysilar? [Middle]**

**5. WeakMap va Map farqi nima? Qachon WeakMap ishlatish kerak? [Middle+]**

**6. Bu kodda memory leak bormi? Toping va tuzating. [Middle+]**

```javascript
function createCounter() {
  const history = [];
  let count = 0;

  return {
    increment() {
      count++;
      history.push({ value: count, timestamp: Date.now() });
    },
    getCount() { return count; },
    getHistory() { return history; }
  };
}

const counter = createCounter();
setInterval(() => counter.increment(), 100);
```

**7. WeakRef nima? Qachon ishlatiladi? [Middle+]**

**8. Chrome DevTools da memory leak qanday topiladi? [Middle+]**

**9. V8 da Generational GC nima? Young va Old Generation farqi? [Senior]**

**10. `structuredClone` va `JSON.parse(JSON.stringify())` farqi nima? [Middle]**

**11. Object pooling nima? Qachon ishlatiladi? [Senior]**

**12. FinalizationRegistry nima? Real-world use case ayting. [Senior]**

**13. `AbortController` event listener cleanup uchun qanday ishlatiladi? [Middle+]**

**14. `deepClone` funksiyasini implement qiling [Senior]**

**Savol:** `structuredClone` ishlatmasdan, circular reference'larni ham qo'llab-quvvatlaydigan `deepClone` yozing.

**15. React useEffect da memory leak qanday oldini olish mumkin? [Middle+]**

**16. V8 da xotirani monitoring qilish va profiling qanday qilinadi? (Node.js) [Senior]**

**17. TypedArray nima? Oddiy Array'dan qachon va nima uchun afzal (masalan katta hajmdagi sonli ma'lumotlar uchun)? [Middle+]**


## 17. Type Coercion va Equality

**1. `==` va `===` farqi nima? Qachon `==` ishlatish mumkin? [Junior+]**

**2. typeof operatori haqida nima bilasiz? typeof null nima qaytaradi va nima uchun? [Junior+]**

**3. Truthy va Falsy qiymatlar nima? Falsy qiymatlarni sanab bering [Junior+]**

**4. Type coercion nima? Explicit va implicit farqi? [Junior+]**

**5. ToPrimitive qanday ishlaydi? Symbol.toPrimitive nima? [Middle+]**

**6. `null` va `undefined` farqi nima? ToNumber da qanday farq qiladi? [Junior+]**

**7. Symbol nima? Nima uchun kerak? [Middle]**

**8. BigInt nima? Number dan farqi? [Middle]**

**9. Map va Object farqi nima? Qachon qaysi birini ishlatish kerak? [Middle]**

**10. WeakMap va Map farqi nima? Qachon WeakMap ishlatiladi? [Middle+]**

**11. `structuredClone()` nima? `JSON.parse(JSON.stringify())` dan farqi? [Middle]**

**12. `Object.is()` nima? `===` dan farqi? [Middle+]**

**13. Set nima? Array dan farqi? Duplikatlarni qanday olib tashlash mumkin? [Junior+]**

**14. NaN nima? Qanday tekshiriladi? Nima uchun NaN === NaN false? [Middle]**

**15. `instanceof` implement qiling [Middle+]**

**16. `||`, `&&`, `??` operatorlarining farqi nima? [Middle]**

**17. Quyidagi kodda xato toping va tuzating [Middle+]**

```javascript
// ❌ Xatoli kod:
function processInput(value) {
  if (!value) {
    return "No input";
  }
  if (typeof value === "object") {
    return Object.keys(value).join(", ");
  }
  return String(value);
}

processInput(0);      // "No input" ← BUG! 0 valid input bo'lishi mumkin
processInput("");     // "No input" ← BUG! "" valid string
processInput(null);   // "No input" ← OK
processInput(null);   // lekin typeof null === "object" ga yetmaydi
```

**18. `deepEqual` implement qiling — ikki qiymatni chuqur taqqoslash [Senior]**

**19. ToString va ToNumber coercion qoidalari object'ni primitive'ga aylantirishda qanday ishlaydi? [Middle]**

**20. JavaScript'dagi barcha primitive type'larni sanab bering. Nechta primitive type bor? [Junior+]**


## 18. DOM Manipulation

**1. DOM nima? HTML bilan farqi nima? [Junior+]**

**2. `childNodes` va `children` farqi nima? [Junior+]**

**3. `querySelector` va `getElementById` farqi nima? [Junior+]**

**4. `textContent`, `innerHTML`, `innerText` farqi nima? [Junior+]**

**5. `closest()` va `matches()` nima? [Middle]**

**6. `data-*` attributes va `dataset` qanday ishlaydi? [Junior+]**

**7. `classList` API ni tushuntiring [Junior+]**

**8. Xato toping — Live collection bilan loop [Middle]**

```javascript
// Bu kod barcha elementlarni o'chirmaydi — nima uchun?
const items = document.getElementsByClassName("item"); // LIVE!
for (let i = 0; i < items.length; i++) {
  items[i].remove();
}
```

**9. Reflow va Repaint nima? Layout Thrashing qanday bo'ladi? [Middle+]**

**10. DocumentFragment nima? Nima uchun kerak? [Middle]**

**11. `requestAnimationFrame` nima? `setInterval` dan farqi? [Middle]**

**12. `cloneNode` qanday ishlaydi? Event listener'lar nusxalanadimi? [Middle]**

**13. Xato toping — XSS xavfli kod [Middle+]**

```javascript
function showProfile(user) {
  const container = document.getElementById("profile");
  container.innerHTML = `
    <h2>${user.name}</h2>
    <p>Bio: ${user.bio}</p>
    <a href="${user.website}">Website</a>
  `;
}

showProfile({
  name: '<script>alert("hacked")</script>',
  bio: '<img src=x onerror="document.cookie">',
  website: 'javascript:alert(1)'
});
```

**14. Coding: 10,000 elementni performance-optimal qo'shing [Senior]**

**15. Virtual DOM nima? DocumentFragment dan farqi? [Senior]**

**16. `insertAdjacentHTML` qanday ishlaydi? 4 ta pozitsiyani ayting [Middle]**

**17. `getComputedStyle` va `style` farqi nima? [Middle]**

**18. Element yaratish va qo'shish usullarini solishtiring [Junior+]**

**19. Coding: Todo list — DOM manipulation bilan [Middle+]**

**20. DOM'dagi asosiy Node turlari (Element, Text, Comment va h.k.) qanday farqlanadi? `nodeType` qanday ishlatiladi? [Junior+]**


## 19. Events

**1. Event Bubbling va Capturing nima? Tartibini ayting [Junior+]**

**2. `stopPropagation()` vs `preventDefault()` farqi nima? [Middle]**

**3. Event Delegation nima? Qanday implement qilinadi? [Middle]**

**4. `event.target` vs `event.currentTarget` farqi [Junior+]**

**5. Xato toping — delegation da target tekshirish [Middle]**

```javascript
document.body.addEventListener("click", (e) => {
  if (e.target.classList.contains("delete-btn")) {
    const row = e.target.parentElement.parentElement;
    row.remove();
  }
});
```

**6. Custom Events qanday yaratiladi? [Middle+]**

**7. `removeEventListener` nima uchun ishlamayapti? [Junior+]**

**8. Passive event listener nima? Nima uchun kerak? [Middle+]**

**9. Event listener va memory leak. Qanday oldini olish mumkin? [Middle]**

**10. Keyboard events: `e.key` vs `e.code` farqi [Junior+]**

**11. Touch va Pointer Events farqi [Senior]**

**12. Coding: Debounced search handler [Middle+]**

**13. addEventListener options to'liq ro'yxatini ayting [Senior]**

**14. Xato toping — `var` bilan loop ichida handler [Middle]**

```javascript
const buttons = document.querySelectorAll("button");
for (var i = 0; i < buttons.length; i++) {
  buttons[i].addEventListener("click", () => {
    console.log("Button:", i);
  });
}
// Barcha buttonlar oxirgi qiymat ko'rsatadi!
```

**15. `return false` addEventListener da ishlaydimi? [Junior+]**

**16. Coding: EventEmitter implement qiling [Middle+]**

**17. SPA da event listener cleanup pattern [Senior]**

**18. Coding: Event delegation bilan Tab Component [Middle]**

**19. Event handler ishga tushishi (masalan, click) macrotask sifatida navbatga qo'shiladi — bu Promise microtask'lari bilan qanday tartibda bajariladi? [Middle+]**


## 20. Browser APIs

**1. Fetch API da HTTP error handling qanday qilinadi? [Junior+]**

**2. AbortController nima? Qanday ishlatiladi? [Middle]**

**3. `localStorage` vs `sessionStorage` vs `cookies` farqi [Junior+]**

**4. IntersectionObserver nima? Lazy loading qanday qilinadi? [Middle]**

**5. Web Worker nima? Qachon ishlatiladi? [Middle]**

**6. WebSocket vs SSE (Server-Sent Events) farqi [Middle+]**

**7. MutationObserver nima uchun kerak? [Middle]**

**8. History API SPA routing uchun qanday ishlatiladi? [Middle+]**

**9. Xato toping — FormData bilan Content-Type [Middle]**

```javascript
const formData = new FormData();
formData.append("name", "Ali");
formData.append("avatar", fileInput.files[0]);

await fetch("/api/upload", {
  method: "POST",
  headers: { "Content-Type": "multipart/form-data" },
  body: formData
});
```

**10. Blob va File API qanday ishlaydi? [Middle]**

**11. Transferable Objects nima? [Senior]**

**12. `performance.now()` vs `Date.now()` farqi [Junior+]**

**13. Cookie attributes nima? CSRF himoya qanday? [Middle+]**

**14. Coding: Fetch wrapper bilan retry logic [Middle+]**

**15. ResizeObserver va `window.onresize` farqi [Middle]**

**16. Coding: Infinite Scroll implement qiling [Middle+]**

**17. Service Worker qanday ishlaydi? Lifecycle? [Senior]**

**18. Web Crypto API nima uchun kerak? [Middle]**

**19. IndexedDB qachon localStorage o'rniga ishlatiladi? [Middle]**

**20. Fetch Response body faqat bir marta o'qilishi mumkinligi nimani anglatadi? Buni qanday hal qilish mumkin (masalan `clone()` bilan)? [Middle]**

**21. URLSearchParams va URL API nima uchun kerak? Query string bilan ishlashni qanday osonlashtiradi? [Junior+]**

**22. PerformanceObserver nima uchun ishlatiladi? `performance.now()` dan farqi nima? [Middle+]**

**23. Geolocation, Clipboard va Notification API'lar nima uchun ishlatiladi? Ular ishlashi uchun foydalanuvchidan nima talab qilinadi? [Junior+]**


## 21. Error Handling

**1. JavaScript dagi asosiy Error turlari qaysilar va farqlari nima? [Junior+]**

**2. Nima uchun Error throw qilish kerak, string emas? [Junior+]**

**3. Custom Error class qanday yaratiladi? [Middle]**

**4. Error.cause nima va qanday ishlatiladi? [Middle]**

**5. Bu kodda nima xato va qanday tuzatiladi? [Middle]**

**6. unhandledrejection eventi nima va qanday ishlatiladi? [Middle+]**

**7. Re-throwing pattern nima? Qachon ishlatiladi? [Middle+]**

**8. Result pattern nima? throw dan qanday farq qiladi? [Senior]**

**9. Operational vs Programmer errors farqi nima? [Senior]**

**10. Circuit Breaker pattern'ini tushuntiring va implement qiling [Senior]**

**11. Graceful degradation pattern'ini tushuntiring [Senior]**

**12. retry funksiyasini exponential backoff bilan implement qiling [Middle+]**

**13. window.onerror vs addEventListener("error") farqi nima? [Middle+]**

**14. Promise.allSettled vs Promise.all — error handling farqi? [Middle]**

**15. Error handling best practices ro'yxatini ayting [Senior]**

**16. try/catch/finally bloklari qanday ishlaydi? `finally` qachon va nima uchun har doim bajariladi? [Junior+]**

**17. Async funksiyada `try/catch` orqali qanday xatolar ushlanadi — `await` qilingan Promise reject bo'lsa-chi? [Middle]**


## 22. Modern JavaScript (ES6+)

**1. Destructuring nima va qanday turlariga bo'linadi? [Junior+]**

**2. Spread va Rest operatorlarining farqi nima? [Junior+]**

**3. Tagged template nima va real-world da qayerda ishlatiladi? [Middle]**

**4. `?.` (optional chaining) va `??` (nullish coalescing) farqi nima? [Junior+]**

**5. Default parameter qachon ishlaydi, qachon ishlamaydi? [Middle]**

**6. Bu kodda nima xato? [Middle]**

**7. `for...of` va `for...in` qachon ishlatiladi? [Junior+]**

**8. `||=`, `&&=`, `??=` operator'larini tushuntiring [Middle]**

**9. JSON.stringify qaysi qiymatlarni skip qiladi? [Middle]**

**10. JSON.stringify ning replacer va space argumentlarini tushuntiring [Middle+]**

**11. RegExp named groups va matchAll nima? [Middle]**

**12. Lookbehind va Lookahead nima? Misol bering [Senior]**

**13. `String.raw` nima va qachon ishlatiladi? [Middle]**

**14. Swap, filter, va clean object — destructuring bilan qanday qilinadi? [Junior+]**

**15. ES6+ xususiyatlardan qaysilari eng ko'p ishlatiladi va nima uchun? [Senior]**

**16. Destructuring'da default qiymat faqat qachon ishga tushadi — `undefined` uchunmi yoki `null` uchun ham? [Middle]**

**17. `||` va `??` operatorlari orasidagi farq nima? Qaysi holatlarda ular boshqacha natija beradi? [Middle]**

**18. Numeric separators (masalan `1_000_000`) nima uchun kerak? [Junior+]**


## 23. Array Methods Mastery

**1. map, filter, reduce farqi nima? [Junior+]**

**2. find vs filter — qachon qaysi birini ishlatish kerak? [Junior+]**

**3. ES2023 immutable array methods qaysilar? [Middle]**

**4. some va every nima? Bo'sh array uchun nima qaytaradi? [Middle]**

**5. includes vs indexOf farqi nima? [Junior+]**

**6. Array.prototype.map polyfill yozing [Middle]**

**7. Array.prototype.reduce polyfill yozing [Middle+]**

**8. flat() ni implement qiling [Middle+]**

**9. at() method nima? arr[-1] nima uchun ishlamaydi? [Junior+]**

**10. forEach dan break qilish mumkinmi? [Middle]**

**11. fill() bilan reference type muammosi nima? [Middle+]**

**12. reduce bilan qanday real-world pattern'lar qilish mumkin? [Senior]**

**13. Array.prototype.sort() default holatda elementlarni qanday saralaydi (sonlar uchun ham) va bu nima uchun kutilmagan natija berishi mumkin? [Middle]**

**14. flatMap() nima? map().flat() dan farqi va afzalligi bormi? [Middle]**

**15. Array method'lar orasida (masalan oddiy `for` loop vs `map`/`forEach`) performance farqi bormi? Katta array'larda nimaga e'tibor berish kerak? [Middle+]**


## 24. Proxy va Reflect

**1. Proxy nima va u qanday ishlaydi? [Junior+]**

**2. Proxy ning 13 ta trap'ini sanab bering [Middle]**

**3. Reflect nima va nima uchun Proxy ichida ishlatish kerak? [Middle]**

**4. set trap da nima uchun true qaytarish kerak? [Middle]**

**5. Proxy invariants nima? Misol bilan tushuntiring [Senior]**

**6. Proxy.revocable() nima va qachon ishlatiladi? [Middle+]**

**7. Proxy bilan private field (#) muammosi nima? Qanday hal qilasiz? [Senior]**

**8. Vue 3 reactivity Proxy asosida qanday ishlaydi? [Middle+]**

**9. Negative array indexing qanday implement qilasiz? [Middle+]**

**10. Bu kodda nima xato? Proxy + frozen object [Senior]**

**11. Proxy performance haqida nima bilasiz? Qachon ishlatmaslik kerak? [Senior]**

**12. createObservable implement qiling [Middle+]**

**13. Reflect.get va target[prop] farqi nima? [Middle+]**

**14. Proxy trap'laridagi `receiver` argumenti nima uchun kerak va uni e'tiborsiz qoldirsak nima bo'ladi? [Senior]**


## 25. Design Patterns

**1. Design pattern nima va nima uchun kerak? [Junior+]**

**2. Factory pattern nima? Qachon ishlatiladi? [Junior+]**

**3. Singleton pattern nima? JavaScript da qanday implement qilasiz? [Middle]**

**4. Observer va Pub/Sub pattern farqi nima? [Middle+]**

**5. EventEmitter implement qiling [Middle+]**

**6. Strategy pattern qachon ishlatiladi? Misol bering [Middle]**

**7. Decorator pattern nima? JavaScript da qanday ishlaydi? [Middle]**

**8. Module pattern qanday ishlaydi? IIFE vs ES Module [Middle]**

**9. Middleware pipeline implement qiling [Senior]**

**10. Command pattern nima? Undo/redo qanday ishlaydi? [Middle+]**

**11. Facade pattern nima? Real-world misol bering [Junior+]**

**12. State pattern va if/else farqi nima? [Middle+]**

**13. Builder pattern qachon ishlatiladi? [Middle]**

**14. Adapter pattern real-world misol bering [Middle]**

**15. Chain of Responsibility va Middleware farqi bormi? [Senior]**

**16. Qaysi pattern'ni qachon ishlatish kerak? [Senior]**


## 26. String Methods

**1. String primitive va String object farqi nima? [Junior]**

**2. slice() va substring() farqi nima? [Junior+]**

**3. indexOf va includes farqi nima? Qaysi birini qachon ishlatish kerak? [Junior]**

**4. replace() va replaceAll() farqi nima? [Junior+]**

**5. "😀".length nima qaytaradi va nima uchun? [Middle]**

**6. String ni Unicode-safe teskari aylantiring [Middle]**

**7. match() va matchAll() farqi nima? [Middle]**

**8. Template literal va oddiy string farqi nima? [Junior]**

**9. normalize() nima uchun kerak? Real-world misol bering [Middle+]**

**10. String concatenation performance — qaysi usul tez? [Middle]**

**11. isWellFormed() va toWellFormed() nima? [Senior]**

**12. Tagged template literal nima? Misol bering [Middle+]**

**13. at() method nima? charAt() dan farqi? [Junior+]**

**14. String'lar ustida `for...of` bilan iteratsiya qanday ishlaydi — UTF-16 code unit asosidami yoki Unicode code point asosidami? [Middle]**

**15. `padStart()`, `padEnd()` va `repeat()` metodlari nima uchun ishlatiladi? Amaliy misol bering [Junior+]**


## 27. Date va Intl API

**1. Date object ichida nima saqlanadi? [Junior]**

**2. new Date() va Date() farqi nima? [Junior+]**

**3. Nima uchun getMonth() 0-based? new Date(2024, 3, 1) — bu qaysi oy? [Junior+]**

**4. Ikki Date objectni qanday solishtirish kerak? [Junior+]**

**5. "2024-03-13" va "2024-03-13T00:00:00" parse qilishda qanday farq bor? [Middle+]**

**6. Date.now() va new Date().getTime() farqi bormi? [Junior+]**

**7. Intl.DateTimeFormat nima? toLocaleDateString dan farqi? [Middle]**

**8. Intl.NumberFormat bilan valyutani qanday formatlaysiz? [Middle]**

**9. Intl.Collator nima? Oddiy sort() dan farqi nima? [Middle]**

**10. Intl.Segmenter nima? Qachon kerak? [Middle+]**

**11. Temporal API nima? Date dan nima farq qiladi? [Senior]**

**12. Intl.RelativeTimeFormat qanday ishlaydi? [Middle]**

**13. Oyning oxirgi kunini qanday topasiz? [Middle]**

**14. Intl.NumberFormat bilan raqamni compact formatda qanday chiqarasiz? [Junior+]**

**15. Date object'ni nima uchun mutate qilmaslik kerak? Qanday oldini olasiz? [Middle+]**

**16. UTC va Local Time orasidagi farq nima? Date object bu ikkisini qanday boshqaradi (`getTimezoneOffset`)? [Middle]**


## 28. ES2024+ va Kelgusi Standartlar

**1. Object.groupBy() nima? reduce bilan farqi? [Junior+]**

**2. Promise.withResolvers() nima? Qanday ishlatiladi? [Middle]**

**3. ES2025 Set method'lari haqida gapiring. Qanday method'lar bor? [Middle]**

**4. Iterator Helpers nima? Array method'lardan farqi? [Middle+]**

**5. using keyword nima? try/finally dan farqi? [Senior]**

**6. Map.groupBy() va Object.groupBy() farqi nima? Qachon qaysi birini ishlatish kerak? [Middle+]**

**7. Import Attributes nima? Nima uchun kerak? [Middle]**

**8. isWellFormed() va toWellFormed() nima? Qachon kerak? [Middle+]**

**9. Symbol.dispose va Symbol.asyncDispose farqi nima? [Senior]**

**10. RegExp v flag u flag dan nima farq qiladi? [Senior]**

**11. Array.fromAsync va Promise.all farqi nima? [Middle+]**

**12. TC39 process nima? Stage lar nima? [Junior+]**

**13. Duplicate Named Capturing Groups nima? [Middle]**

**14. DisposableStack nima? [Senior]**

**15. Atomics.waitAsync nima uchun kerak? SharedArrayBuffer bilan qanday bog'liq? [Senior]**

