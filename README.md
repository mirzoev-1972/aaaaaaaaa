# JavaScript Utils

Простая коллекция функций на JavaScript для работы со строками и числами.

```js
// js-utils.js
// Простые утилиты JavaScript: сумма, ограничение значений и обработка строк

// Сумма чисел
function sum(...nums) {
  return nums.reduce((a, b) => a + Number(b || 0), 0);
}

// Ограничение значения в пределах min и max
function clamp(value, min, max) {
  const v = Number(value);
  if (Number.isNaN(v)) return min;
  if (min > max) [min, max] = [max, min];
  return Math.min(Math.max(v, min), max);
}

// Первая буква заглавная
function capitalize(str = '') {
  return str.charAt(0).toUpperCase() + str.slice(1);
}

// Простейший slugify: кириллица → латиница, пробелы → дефис
function slugify(str = '') {
  const from = "абвгдеёзийклмнопрстуфхцчшщъыьэюя";
  const to   = "abvgdeezijklmnoprstufhccshsch'y'eua";
  str = str.toLowerCase().trim();
  let res = '';
  for (const ch of str) {
    const i = from.indexOf(ch);
    res += i !== -1 ? to[i] : ch;
  }
  return res.replace(/[^a-z0-9\s-]/g, '').replace(/\s+/g, '-').replace(/-+/g, '-');
}

// Пример использования
console.log(sum(2, 5, 3));        // 10
console.log(clamp(12, 0, 10));    // 10
console.log(capitalize('hello')); // Hello
console.log(slugify('Привет мир'));// privet-mir
