# ⚡ Elementor Fluid Adaptive Mixin

[Русская версия](#-elementor-fluid-adaptive-mixin) | [English version](#-elementor-fluid-adaptive-mixin-1)

---

<p align="center">
  <img src="assets/Elementor%20Fluid%20Adaptive%20Mixin.png" alt="Elementor Fluid Adaptive Mixin">
</p>

---

## 🇷🇺 Elementor Fluid Adaptive Mixin

**Elementor Fluid Adaptive Mixin** — универсальный LESS-миксин для плавной адаптивной вёрстки без десятков медиазапросов.  
Он автоматически рассчитывает значения CSS-свойств между двумя брейкпоинтами и делает интерфейс плавным, резиновым и pixel-perfect.

---

### 🚀 Основная идея

Обычный адаптив:

- требует много медиазапросов  
- сложно поддерживается  
- создаёт скачки размеров  
- ломается при правках дизайна  

**Fluid-подход**

- масштабирует значения плавно  
- уменьшает код  
- делает верстку стабильнее  
- упрощает поддержку проекта  

---

### ⚙️ Формула

```
min + (max − min) × ((viewport − minScreen) / (maxScreen − minScreen))
```

| Экран | Результат |
|------|-----------|
> maxScreen | max |
< minScreen | min |
между | плавное значение |

---

### 🧠 Как работает

Используется CSS функция:

```
clamp(min, fluid, max)
```

Она ограничивает значение сверху и снизу, а динамическая часть вычисляется через:

```
calc()
```

---

### 📦 Миксин

```less
.fluid(@prop,@max,@min,@maxScreen,@minScreen){
@range:(@maxScreen - @minScreen);
@{prop}:@max;
@media (max-width:~"@{maxScreen}px"){
@{prop}:clamp(@min,calc(@min + (@max - @min) * ((100vw - ~"@{minScreen}px") / @range)),@max);
}
@media (max-width:~"@{minScreen}px"){
@{prop}:@min;
}}
```

---

### 📘 Параметры

| Параметр | Описание |
|---------|----------|
| prop | CSS свойство |
| max | значение на большом экране |
| min | значение на маленьком |
| maxScreen | верхний breakpoint |
| minScreen | нижний breakpoint |

---

### 🧪 Пример

```less
.title{
.fluid(font-size,42px,22px,1920,480);
}
```

Результат  
1920px → 42px  
480px → 22px  
между ними — плавное масштабирование

---

### 🧩 Использование в Elementor

1. Подключить LESS через тему или плагин кастомного CSS  
2. Добавить миксин глобально  
3. Открыть виджет  
4. Advanced → Custom CSS  
5. Вставить:

```css
selector{
.fluid(font-size,40px,18px,1440,768);
}
```

---

### 🎯 Где применять

Подходит для любых числовых свойств:

- font-size  
- margin / padding  
- width / height  
- gap  
- border-radius  
- line-height  
- layout размеров  

---

### ✅ Преимущества

- меньше медиазапросов  
- плавный UI  
- чище код  
- быстрее разработка  
- универсальность  
- production ready  

---

---

## 🇺🇸 Elementor Fluid Adaptive Mixin

**Elementor Fluid Adaptive Mixin** is a universal LESS mixin for fluid responsive scaling without tons of media queries.  
It automatically calculates CSS property values between two breakpoints and makes UI smooth and predictable.

---

### 🚀 Concept

Classic responsive design:

- many breakpoints  
- hard maintenance  
- layout jumps  
- difficult pixel precision  

Fluid approach:

- smooth scaling  
- less code  
- stable layout  
- easier maintenance  

---

### ⚙️ Formula

```
min + (max − min) × ((viewport − minScreen) / (maxScreen − minScreen))
```

| Screen | Result |
|-------|--------|
> maxScreen | max |
< minScreen | min |
between | interpolated |

---

### 📦 Mixin

```less
.fluid(@prop,@max,@min,@maxScreen,@minScreen){
@range:(@maxScreen - @minScreen);
@{prop}:@max;
@media (max-width:~"@{maxScreen}px"){
@{prop}:clamp(@min,calc(@min + (@max - @min) * ((100vw - ~"@{minScreen}px") / @range)),@max);
}
@media (max-width:~"@{minScreen}px"){
@{prop}:@min;
}}
```

---

### 🧪 Usage

```less
.title{
.fluid(font-size,42px,22px,1920,480);
}
```

---

### ⭐ Advantages

- fewer media queries  
- smooth scaling  
- faster development  
- clean code  
- universal usage  
- production ready  

---

## 👨‍💻 Автор

**Сергей Солошенко (RuCoder)**  
🛠 WordPress / Full Stack  
📬 support@рукодер.рф  
📲 Telegram: @RussCoder  

Если нужна кастомизация под проект или установка под ключ — пишите в личные сообщения.
