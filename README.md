````markdown
# Elementor Fluid Adaptive Mixin
[Русская версия](#-elementor-fluid-adaptive-mixin) | [English version](#-elementor-fluid-adaptive-mixin-1)
---
<p align="center"><img src="assets/Elementor Fluid Adaptive Mixin.png" alt="Elementor Fluid Adaptive Mixin Banner"></p>
---
# 🇷🇺 Elementor Fluid Adaptive Mixin
**Elementor Fluid Adaptive Mixin** — универсальный LESS-миксин для плавной адаптивной вёрстки без множества медиазапросов. Он автоматически рассчитывает значения CSS-свойств между двумя брейкпоинтами и делает интерфейс полностью резиновым, плавным и предсказуемым.
## 📌 Зачем нужен
Классический адаптив требует десятки медиазапросов, усложняет поддержку, ломается при изменении макета и создаёт резкие скачки размеров. Fluid-подход решает это — значения масштабируются плавно, дизайн остаётся pixel-perfect, код сокращается, поддержка упрощается и разработка ускоряется.
## ⚙️ Что делает код
Формула расчёта: `min + (max − min) × ((viewport − minScreen) / (maxScreen − minScreen))` — свойство равно max на большом экране, равно min на маленьком и плавно меняется между ними.
## 🧠 Как работает
Используется CSS-функция `clamp(min, fluid, max)` которая ограничивает значение сверху и снизу. Внутри применяется `calc()` для динамического вычисления.
## 📦 Миксин
```less
.fluid(@prop,@max,@min,@maxScreen,@minScreen){@range:(@maxScreen - @minScreen);@{prop}:@max;@media (max-width:~"@{maxScreen}px"){@{prop}:clamp(@min,calc(@min + (@max - @min) * ((100vw - ~"@{minScreen}px") / @range)),@max);} @media (max-width:~"@{minScreen}px"){@{prop}:@min;}}
```
## 📘 Параметры
prop — CSS свойство | max — значение на большом экране | min — значение на маленьком | maxScreen — верхний брейкпоинт | minScreen — нижний брейкпоинт
## 🧪 Пример
```less
.title{.fluid(font-size,42px,22px,1920,480);}
```
Результат: 1920px → 42px, 480px → 22px, между ними плавное масштабирование.
## 🧩 Использование в Elementor
1) Подключите LESS через тему или плагин кастомного CSS  
2) Добавьте миксин глобально  
3) В Elementor откройте виджет → Advanced → Custom CSS  
4) Вставьте:
```css
selector{.fluid(font-size,40px,18px,1440,768);}
```
## 🎯 Где применять
Подходит для font-size, margin, padding, width, height, gap, border-radius, line-height и любых числовых CSS свойств.
## 🚀 Преимущества
✔ меньше медиазапросов ✔ плавный UI ✔ чище код ✔ быстрее разработка ✔ универсальность ✔ production ready
---
# 🇬🇧 Elementor Fluid Adaptive Mixin
**Elementor Fluid Adaptive Mixin** is a universal LESS mixin for smooth responsive scaling without tons of media queries. It automatically calculates CSS property values between two breakpoints and makes UI fluid and predictable.
## 📌 Why
Classic responsive design requires many breakpoints, is hard to maintain, breaks easily and jumps between sizes. Fluid approach gives smooth scaling, pixel-perfect layout, less code and easier maintenance.
## ⚙️ Formula
`min + (max − min) × ((viewport − minScreen) / (maxScreen − minScreen))` — property equals max on large screens, min on small and scales between.
## 📦 Mixin
```less
.fluid(@prop,@max,@min,@maxScreen,@minScreen){@range:(@maxScreen - @minScreen);@{prop}:@max;@media (max-width:~"@{maxScreen}px"){@{prop}:clamp(@min,calc(@min + (@max - @min) * ((100vw - ~"@{minScreen}px") / @range)),@max);} @media (max-width:~"@{minScreen}px"){@{prop}:@min;}}
```
## 🧪 Usage
```less
.title{.fluid(font-size,42px,22px,1920,480);}
```
## 🎯 Best for
Typography, spacing, layout scaling, containers, grids and UI systems.
## 🚀 Advantages
✔ fewer media queries ✔ smooth UI ✔ faster development ✔ clean code ✔ universal ✔ production ready
---
## 👨‍💻 Автор
**Сергей Солошенко (RuCoder)**  
🛠 WordPress / Full Stack  
📬 support@рукодер.рф  
📲 Telegram: @RussCoder  
Если нужна кастомизация под проект или установка под ключ — пишите в личные сообщения.
````
