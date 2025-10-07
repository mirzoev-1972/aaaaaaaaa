# 🌟 JavaScript Utils

Простая коллекция полезных функций на чистом *JavaScript* — для чисел и строк.  
Минимализм, читаемость и удобство 💡

---

### 🚀 Возможности
- 🔢 *sum(...)* — считает сумму чисел  
- ⚖ *clamp(value, min, max)* — ограничивает значение диапазоном  
- 🔠 *capitalize(str)* — делает первую букву заглавной  
- 🌐 *slugify(str)* — преобразует кириллицу в латиницу и пробелы в дефисы

---

### 💻 Код

```js
function sum(...nums) {
  return nums.reduce((a, b) => a + Number(b || 0), 0);
}

function clamp(value, min, max) {
  const v = Number(value);
  if (Number.isNaN(v)) return min;
  if (min > max) [min, max] = [max, min];
  return Math.min(Math.max(v, min), max);
}

function capitalize(str = '') {
  return str.charAt(0).toUpperCase() + str.slice(1);
}

function slugify(str = '') {
  const from = "абвгдеёзийклмнопрстуфхцчшщъыьэюя";
  const to   = "abvgdeezijklmnoprstufhccshsch'y'eua";
  str = str.toLowerCase().trim();
  let res = '';
  for (const ch of str) {
    const i = from.indexOf(ch);
    res += i !== -1 ? to[i] : ch;
  }
  return res
    .replace(/[^a-z0-9\s-]/g, '')
    .replace(/\s+/g, '-')
    .replace(/-+/g, '-');
}

console.log(sum(2, 5, 3));
console.log(clamp(12, 0, 10));
console.log(capitalize('hello'));
console.log(slugify('Привет мир'));
