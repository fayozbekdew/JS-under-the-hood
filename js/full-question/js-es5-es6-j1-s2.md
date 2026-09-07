# JavaScript (ES5 & ES6+) — J1 dan S2 gacha Interview Question Bank

> Source: [Andersen People — Knowledge Matrix](https://people-andersenlab.com/knowledge-matrix) — "JS (ES5)" va "JS (ES6+)" skill category'lari, J1 dan S2 gacha barcha darajalar. Har bir daraja sahifasi alohida ko'rib chiqilib, takrorlanmaydigan (deduplicated) yagona ro'yxatga birlashtirildi — har bir savol qaysi darajada birinchi marta talab qilinishini ko'rsatuvchi teg bilan ([J1]...[S2], Andersen'ning o'z daraja nomlanishi: J = Junior, M = Middle, S = Senior). Faqat savollar (javobsiz), AI bilan mock interview uchun.

## Mundarija

1. [JS (ES5)](#1-js-es5) — 37 savol
2. [JS (ES6+)](#2-js-es6) — 22 savol

---

## 1. JS (ES5)

### Common

**1. Sikllar (`while`, `for`), `if` sharti, `switch` konstruksiyasi, mantiqiy va shartli operatorlar, `alert`/`prompt`/`confirm`, strict va non-strict taqqoslash (`==` vs `===`), hoisting — bularning barchasini tushuntirib bera olasizmi? [J1]**

**2. `var` bilan e'lon qilingan o'zgaruvchi `var`siz e'lon qilingan o'zgaruvchidan (implicit global) nima farq qiladi? `"use strict"` nima uchun kerak? [J3]**

**3. "eval is evil" deyilishining sababi nima? [S2]**

### Objects

**4. Object property/method'larini set/get/delete qilish, object key'larini olish, `for...in` sikli va object yaratishning turli usullari qanday ishlaydi? [J1]**

**5. Object'dan primitive'ga konversiya (`ToPrimitive`) qanday ishlaydi? Object descriptor, getter/setter, object'ni copy/clone qilish (object pointer tushunchasi) va mutable/immutable object'lar nima? [J3]**

**6. Deep copy/clone qanday amalga oshiriladi? Object'lar asosida linked list qanday quriladi? [M3]**

**7. Garbage Collector nima va nima uchun kerak? [J1]**

**8. "Mark and sweep" algoritmi qanday ishlaydi? Object pointer'ning "reachability"si nima va uni garbage collector uchun qanday belgilaymiz? [J3]**

**9. Generational, incremental va idle-time garbage collection nima? [M3]**

### Data types

**10. JavaScript'dagi barcha data type'lar ro'yxatini ayting. [J1]**

**11. Type conversion (tur konversiyasi) qanday ishlaydi? `typeof` operatori qanday ishlatiladi? [J3]**

**12. Sananing yil/oy/kun qismlarini set/get qilish qanday amalga oshiriladi? [J1]**

**13. Sana (Date) qanday parse qilinadi? [J3]**

**14. UTC sanalar va timezone'lar bilan qanday ishlanadi? Object'ning valid Date ekanligini qanday tekshirasiz? [S1]**

**15. Object'larni JSON metodlari (`JSON.stringify`/`JSON.parse`) yordamida qanday clone qilasiz? [J1]**

**16. Object'ni JSON'ga qanday konvert qilasiz? [J3]**

**17. `JSON.parse` metodida callback (reviver) qanday ishlatiladi? [S1]**

### Functions

**18. Funksiya turlari (declaration, expression va h.k.) qaysilar? IIFE (immediately-invoked function expression) nima? [J1]**

**19. Function-constructor nima? "Array-like" argument'lar nima? Rekursiya ta'rifi va misollarini ayting. [J2]**

**20. Object'larni rekursiv tarzda qanday aylanib chiqasiz (recursive traversal)? `new Function` xususiyati nima? Currying nima? [M1]**

**21. `this` nima? Uni funksiyaga qanday bog'lash (bind) mumkin? Global context (`window`) da `this` nimaga teng? [J1]**

**22. Lexical environment va scope ta'riflari qanday? Variable shadowing nima? Closure ta'rifi, misollari va nom to'qnashuvlari (name conflicts) qanday bo'ladi? [J2]**

**23. Lexical environment qanday garbage collect qilinadi (closure orqali xotira ushlab turilishi)? [M1]**

### Prototypes, inheritance

**24. `__proto__` va `prototype` propertylari nima? Prototype chain qanday ishlaydi? Prototype bilan object'ni qanday yaratasiz va prototype'ni qanday olish/o'rnatish mumkin? [J1]**

**25. Prototype-based inheritance OOP (klassik) inheritance'dan nima bilan farq qiladi? Function-constructor yordamida prototype bilan object yaratish (functional prototyping) qanday ishlaydi? [M1]**

**26. Prototype orqali object'ning constructor'ini qanday olish mumkin? [S2]**

### Asynchronous programming

**27. Blocking code nima va u nima uchun muammo? [J1]**

**28. Event loop kontseptsiyasi nima? "Zero delay" (`setTimeout(() => {}, 0)`) va event loop navbati qanday ishlaydi? Macro va micro task'lar farqi nima? [J2]**

**29. JavaScript'da "soxta multithreading" va "concurrency" tushunchasi nimani anglatadi? [M2]**

**30. `setTimeout` va `setInterval` nima uchun kerak? Timeout/interval'larni qanday tozalaysiz (`clearTimeout`/`clearInterval`)? [J1]**

**31. `requestAnimationFrame` nima uchun kerak va uni brauzerlar qanday qo'llab-quvvatlaydi? [M2]**

### Regular expressions

**32. RegExp object'ining ikkita metodi va RegExp yaratishning ikki usuli qanday? Asosiy RegExp pattern'lari (character class'lar) va global/case-insensitive qidiruv qanday ishlaydi? [J1]**

**33. O'rtacha darajadagi RegExp pattern'lari (assertion'lar, quantifier'lar) va belgilarni escape qilish qanday ishlaydi? [J3]**

**34. Ilg'or RegExp pattern'lari (group'lar va range'lar) hamda qo'shimcha qidiruv flag'lari qanday ishlaydi? [M3]**

### Error handling

**35. `try/catch` qanday ishlatiladi? Exception'larni qanday `throw` qilamiz? [J2]**

**36. `try/catch`da `finally` bloki nima uchun kerak? Error object'ining propertylari qaysilar? [M1]**

**37. `window.onerror` global error handler sifatida qanday ishlaydi? [M3]**

## 2. JS (ES6+)

### Common

**1. `let`/`const` bilan `var` orasidagi farq nima? Temporal Dead Zone (TDZ) nima? Destructuring assignment va spread operator qanday ishlaydi? Optional chaining (`?.`) nima? Arrow function oddiy funksiyadan nima bilan farq qiladi? `for...of` sikli, template string, `Object.keys/values/fromEntries/entries` hamda `flat`/`flatMap`/`includes`/`Array.from()` metodlari qanday ishlaydi? [J1]**

**2. `Map`/`Set` nima? `Object.assign` bilan spread operator orasidagi farq nima? Nullish coalescing operatori (`??`) qanday ishlaydi? [J3]**

**3. `WeakMap`/`WeakSet` nima uchun kerak? `Proxy`/`Reflect` nima? Iterable object degani nima? Tagged template function (tag function) nima? [S1]**

### Modules

**4. ES module'larda import/export sintaksisi qanday ishlaydi? `import * as` nima uchun kerak? `import`/`export ... as` qachon ishlatiladi? [J1]**

**5. Default export nima va nima uchun yomon amaliyot hisoblanadi? Re-export nima uchun kerak? [J3]**

**6. Dynamic import (lazy-loaded module'lar) qanday ishlaydi? Module Namespace Export nima? [S1]**

### Classes

**7. Class'larning asosiy sintaksisi qanday? Inheritance (`extends`) qanday ishlaydi? Private va protected property/method'lar qanday yaratiladi? [J1]**

**8. `instanceof` operatori class bilan qanday ishlaydi? Static property va method'lar nima? [J3]**

**9. Class-based inheritance'ni functional inheritance'ga (va aksincha) qanday o'girish mumkin? Mixin nima? Decorator nima? [M3]**

### Network

**10. `fetch()` ning oddiy (basic) ishlatilishi qanday — so'rov yuborish va javobni qayta ishlash? [J1]**

**11. `fetch()` ning ilg'or (advanced) ishlatilishi qanday — response body'dan binary data olish, header'larni get/set qilish? [M1]**

**12. `XMLHttpRequest` (XHR) bilan `fetch()` orasidagi farq nima? [M3]**

### Asynchronous programming

**13. Promise callback'dan nima bilan farq qiladi? Promise'ning holatlari (state'lari) qanday? Xatolarni Promise bilan qanday handle qilamiz? [J3]**

**14. Promise chaining qanday ishlaydi ("falling through" promises)? Custom promise qanday yaratiladi? `.finally()` nima uchun kerak? `.then()` orqali xatoni qanday ushlash mumkin? [M2]**

**15. `Promise.all()` qanday ishlaydi — uni polyfill sifatida qanday yozgan bo'lardingiz? `Promise.race()` va `Promise.allSettled()` metodlari nima? [S1]**

**16. Async funksiyaga misollar keltiring. [J3]**

**17. Promise bilan yozilgan kodni async/await'ga qanday qayta yozish mumkin? Class method'larida async/await qanday ishlatiladi? [M2]**

**18. Async/await "under the hood" qanday ishlaydi? `Promise.all`/`Promise.race`ning async/await bilan analogini qanday yozasiz? [S1]**

**19. Oddiy generator sintaksisi qanday ishlaydi? Generator'larni bir-biriga qanday ulash (composition) mumkin? [M2]**

**20. `next()`ga qiymat yuborish va aksincha `yield` orqali qiymat olish qanday ishlaydi? Iterator'lar nima? Async generator va async iterator'lar qanday ishlaydi? [S1]**

### Data types

**21. `Symbol` type nima uchun kerak? [M1]**

**22. `BigInt` nima va oddiy `Number`dan nima farq qiladi? [S1]**
