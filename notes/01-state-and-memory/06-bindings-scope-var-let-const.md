# Binding، Scope، `var`، `let` و `const`

## Problem

پس از حل مسئله‌ی نگه‌داری State، زبان به ابزارهایی نیاز دارد تا مشخص کند هر نام به چه مقداری متصل
است، این اتصال از کجا قابل دسترسی است، چه زمانی ایجاد می‌شود و آیا می‌توان آن را دوباره به مقدار
دیگری نسبت داد.

## Computational Need

برنامه باید بتواند Bindingهای State را با محدوده‌ی دسترسی و قواعد تغییرپذیری مشخص مدیریت کند. این
قواعد باید از دسترسی‌های مبهم و خطاهای ناشی از استفاده‌ی زودهنگام از Declaration جلوگیری کنند.

## Concept

**Binding** رابطه‌ی میان یک نام و یک مقدار است. **Scope** محدوده‌ای است که در آن Binding قابل دسترسی
است. **Mutability** مشخص می‌کند Binding یا داده‌ی مربوط به آن چگونه می‌تواند تغییر کند.

این لایه از مسیر مفهومی زیر درک می‌شود:

```text
Language
   ↓
Variable Declaration
   ↓
Binding
   ↓
Scope + Lifetime + Mutability
```

## Language Feature

`var` دارای Function Scope است؛ این مدل همیشه با ساختار بلوکی کد مدرن سازگار نیست. `let` و `const`
در ES6، Block Scope را معرفی کردند و Binding آن‌ها پیش از Initialization در **Temporal Dead Zone
(TDZ)** قرار دارد.

Hoisting ذاتاً «خرابی» نیست؛ توصیفی است از این‌که Declarationها پیش از اجرای عادی کد، در Environment
مربوط ثبت یا ایجاد می‌شوند. تفاوت مهم این است که `var` پیش از مقداردهی `undefined` دارد، اما `let` و
`const` تا پیش از Initialization قابل دسترسی نیستند.

`const` خود Object را ثابت نمی‌کند؛ فقط Reassignment همان Binding را ممنوع می‌کند. بنابراین Mutation
داخلی Object همچنان ممکن است:

```js
const user = { age: 20 };
user.age = 21; // مجاز است
// user = { age: 21 }; // خطا
```

برای محدود کردن تغییر Propertyها بحث جداگانه‌ای مانند `Object.freeze()` مطرح است که آن هم به‌صورت
پیش‌فرض Shallow است.

## Syntax

```js
var functionScoped = 1;

{
  let blockScoped = 2;
  const fixedBinding = { value: 3 };
  fixedBinding.value = 4;
}
```

مقایسه‌ی سه Declaration:

| ویژگی                   | `var`           | `let`        | `const`      |
| ----------------------- | --------------- | ------------ | ------------ |
| Scope                   | Function        | Block        | Block        |
| Reassignment            | مجاز            | مجاز         | ممنوع        |
| TDZ                     | ندارد           | دارد         | دارد         |
| Hoisted Declaration     | دارد            | دارد، با TDZ | دارد، با TDZ |
| کاربرد معمول در کد مدرن | معمولاً نامناسب | مناسب        | مناسب        |

## Personal Notes & REPL Verification

`var`، `let` و `const` ابزارهای مدیریت Bindingهای State در لایه‌ی زبان هستند، نه خود Memory
Management. پایان Scope نیز الزاماً به معنی آزاد شدن فوری Memory نیست؛ اگر Closure یا Reference
دیگری به State دسترسی داشته باشد، ممکن است آن State زنده بماند.

| پرسش یا فرضیه                                        | آزمایش در REPL                             | نتیجه‌ی مشاهده‌شده  | درک به‌روزشده                                                               |
| ---------------------------------------------------- | ------------------------------------------ | ------------------- | --------------------------------------------------------------------------- |
| آیا `const` Object را immutable می‌کند؟              | `const user = { age: 20 }; user.age = 21;` | Property تغییر کرد. | `const` Binding را از Reassignment محافظت می‌کند، نه Object را از Mutation. |
| آیا `let` پیش از Declaration مقدار `undefined` دارد؟ | `console.log(value); let value = 10;`      | خطای TDZ رخ می‌دهد. | Binding ایجاد شده، اما پیش از Initialization قابل استفاده نیست.             |
