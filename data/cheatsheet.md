# CSS Cheatsheet

รวมสูตรโกงสำหรับ CSS

## 👍 เว็บไซต์รวบรวมการใช้ CSS

- [https://cssreference.io/](https://cssreference.io/)
- [https://www.w3schools.com/css/default.asp](https://www.w3schools.com/css/default.asp)
- [https://developer.mozilla.org/en-US/docs/Web/CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [https://bulma.io/](https://bulma.io/)
- [https://getbootstrap.com/](https://getbootstrap.com/)

## 🏗️ โครงสร้างของระบบ

```css
/* With selector */
selector {
  property1: value1;
  property2: value2;
}

/* Without selector */
property1: value1; property2: value2;
```

## ⚙️ รูปแบบการใช้งาน

**Inline:**

```html
<body>
  <div style="color: red;">Red text</div>
</body>
```

**Internal:**

```html
<head>
  <style>
    .red-text {
      color: red;
    }
  </style>
</head>

<body>
  <div class="red-text">Red test</div>
</body>
```

**External (แนะนำ):**

```html
<head>
  <link rel="stylesheet" href="path/to/style.css">
</head>

<body>
  <div class="red-text">Red test</div>
</body>
```

## ⏩ Emmet ช่วยให้เขียนโค้ดเร็วขึ้น

<video src="https://i.imgur.com/2PrHHdb.mp4" autoplay muted loop></video>

```html
<!-- .red-text -->
<div class="red-text"></div>

<!-- h1 -->
<h1></h1>

<!-- h1#title.red-text -->
<h1 id="title" class="red-text"></h1>

<!-- h1.red-text*3 -->
<h1 class="red-text"></h1>
<h1 class="red-text"></h1>
<h1 class="red-text"></h1>

<!-- ul>li*3 -->
<ul>
  <li></li>
  <li></li>
  <li></li>
</ul>

<!-- figure>img+figcaption -->
<figure>
  <img src="" alt="">
  <figcaption></figcaption>
</figure>

<!-- img[src="http://via.placeholder.com/150"] -->
<img src="http://via.placeholder.com/150" alt="">

<!-- button{Submit} -->
<button>Submit</button>

<!-- ul>li{Item $}*3 -->
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```

> เรียนรู้เพิ่มเติมได้ที่ [https://emmet.io/](https://emmet.io/)

## 👨‍💻 การเปิด Element ผ่าน DevTools (F12)

![inspect](https://i.imgur.com/Q6pAtyx.jpg)

## 📑 Selector

```css
h1 {}         /* <h1> */
.red-text {}  /* <element class="red-text"> */
#title {}     /* <element id="title"> */
* {}          /* <element> (เลือกทุกตัว) */

h1.red-text {} /* <h1 class="red-text"> */
h1, h2.head {} /* <h1> และ <h2 class="head"> */
```

> ชื่อ class และ id ไม่สามารถตั้งเป็นตัวเลขนำหน้าได้ ใช้ตัวอักษรภาษาอังกฤษเท่านั้น และตัวอักขระ `-` `_`

## 📑 Attribute Selector

```css
[href] {}               /* <a href=""> */
[href="index.html"] {}  /* <a href="index.html"> */
[data-name~="John"] {}  /* <element data-name="Joe John Jane"> */
[data-name|="John"] {}  /* <element data-name="Joe-John-Jane"> */
[href^="http://"] {}    /* <a href="http://example.com"> */
[href$=".org"] {}       /* <a href="https://wikipedia.org"> */
[href*="google"] {}     /* <a href="http://maps.google.com"> */
```

## 📑 Relationship Selector

```html
<style>
  ul li { color: red; }
</style>

<ul>
  <li>สีแดง</li>
  <li>
    สีแดง
    <ol>
      <li>สีแดง</li>
    </ol>
  </li>
</ul>
```

```html
<style>
  ul > li { color: red; }
</style>

<ul>
  <li>สีแดง</li>
  <li>
    สีแดง
    <ol>
      <li>ไม่เปลี่ยนสี</li>
    </ol>
  </li>
</ul>
```

```html
<style>
  img + i { color: red; }
</style>

<img src="" alt="">
<i>สีแดง</i>
<i>ไม่เปลี่ยนสี</i>
```

```html
<style>
  img ~ i { color: red; }
</style>

<img src="" alt="">
<i>สีแดง</i>
<i>สีแดง</i>
```

## Pseudo-classes

```css
a:hover {}    /* เมื่อ <a> ถูกชี้ด้วยเมาส์ (ไม่รองรับบนมือถือ) */
a:active {}   /* เมื่อ <a> ถูกคลิก */
a:visited {}  /* เมื่อ <a> เคยเข้ามาก่อนแล้ว */
*:target {}   /* เมื่อ URL ลงท้าย #name ที่ถูกเลือก (Document fragment) */

input:focus {}        /* เมื่อ <input> กำลังเตรียมพิมพ์ */
form:focus-within {}  /* เมื่อภายใน <form> มีเนื้อหากำลังเตรียมพิมพ์ */
input[type="checkbox"]:checked {}  /* เมื่อ <input type="checkbox"> ถูกเลือก */
input[type="checkbox"]:default {}  /* เมื่อถูกเลือกเริ่มต้นด้วย <input type="checkbox" checked> */
input:enabled {}      /* เมื่อ <input> สามารถใช้งานได้ */
input:disabled {}     /* เมื่อ <input disabled> ไม่สามารถใช้งานได้ */
input:optional {}     /* เมื่อ <input> จะกรอกหรือไม่ก็ได้ */
input:required {}     /* เมื่อ <input required> จำเป็นต้องกรอก */
input:valid {}        /* เมื่อ <input minlength="3"> ใส่ค่าได้ถูกต้อง */
input:invalid {}      /* เมื่อ <input minlength="3"> ใส่ค่าไม่ถูกต้อง */
input[type="number"]:out-of-range {}  /* เมื่อ <input min="3"> ใส่ค่าไม่ถูกต้อง */

li:first-child {}     /* เลือกเฉพาะ li ที่เป็นลูกคนแรก */
li:last-child {}      /* เลือกเฉพาะ li ที่เป็นลูกคนสุดท้าย */
li:nth-child(2) {}    /* เลือกเฉพาะ li ที่เป็นลูกคนที่ 2 */
li:nth-child(odd) {}  /* เลือกเฉพาะ li ที่เป็นลูกจำนวนคี่ */
li:nth-child(even) {} /* เลือกเฉพาะ li ที่เป็นลูกจำนวนคู่ */
li:nth-child(5n) {}   /* เลือกเฉพาะ li ทุกๆคนที่ 5 */
li:nth-child(10+n) {} /* เลือกเฉพาะ li ตั้งแต่คนที่ 10 เป็นต้นไป */
li:only-child {}      /* เลือกเฉพาะ li ที่ต้องเป็นลูกคนเดียว */

a:not(.active) {}     /* เลือก <a> ก็ต่อเมื่อไม่มี class="active" */
```

## Pseudo-elements

```css
p::first-line {}    /* เลือกเฉพาะบรรทัดแรกใน <p> */
p::first-letter {}  /* เลือกเฉพาะอักขระแรกใน <p> */

li::before { content: "" } /* กำหนดเนื้อหาก่อนหน้า <li> */
li::after { content: "" }  /* กำหนดเนื้อหาหลังจาก <li> */
```

## Units

สำหรับการกำหนดขนาดกับ Property ต่างๆ

|Code|การใช้งาน|
|-|-|
|`px`|กำหนดขนาดตาม Pixels|
|`em`|กำหนดขนาดอ้างอิงตาม Font size ของ Parent|
|`rem`|กำหนดขนาดอ้างอิงตาม Font size ของรากฐาน|
|`cm`|เซนติเมตร (`1cm` = `38px`)|
|`in`|นิ้ว (`1in` = `96px`)|
|`vw`|อ้างอิงตามความกว้างหน้า Web Browser|
|`vh`|อ้างอิงตามความสูงหน้า Web Browser|
|`%`|เปอร์เซ็นต์|

## Box Model

```css
width: 150px;       /* ปรับขนาดความกว้าง 150px */
width: 50%;         /* ปรับขนาดความกว้างครึ่งนึงของการแสดงผล Block แบบเต็ม */
height: 150px;      /* ปรับขนาดความสูง 150px */
height: 100vh;      /* ปรับขนาดความสูงเท่ากับขนาดจอ Web Browser แบบพอดี */

min-width: 100px;   /* กำหนดไม่ให้เนื้อหาแคบกว่า 100px */
min-height: 100px;  /* กำหนดไม่ให้เนื้อหาเตี้ยกว่า 100px */
max-width: 300px;   /* กำหนดไม่ให้เนื้อหาขยายกว้างกว่า 300px */
max-height: 300px;  /* กำหนดไม่ให้เนื้อหาขยายสูงกว่า 300px */

overflow: auto;     /* เมื่อเนื้อหาเกินขนาด Element แสดงผล Scrollbar อัตโนมัติ */
overflow-y: scroll; /* แสดงผล Scrollbar ตลอดเวลา */
overflow-x: hidden; /* ซ่อนการแสดงผลของ Scrollbar */

/* Shorthand สำหรับ margin และ padding */
margin,padding: <all>;
margin,padding: <top-bottom> <left-right>;
margin,padding: <top> <left-right> <bottom>;
margin,padding: <top> <right> <bottom> <left>;

margin: 0;      /* ปรับลดทุกมุมไม่ให้ห่างกับ Element อื่นๆ */
margin: auto;   /* ปรับให้อยู่กึ่งกลางในแนวนอน ในกรณีที่เนื้อหาเป็นรูปแบบ Block */
margin-[top,right,bottom,left]: 5px;  /* ปรับระยะห่างมุมใดมุมนึง 5px */

padding: 10px;      /* ขยายขนาดเนื้อหาทุกมุม 10px */
padding: 5px 10px;  /* ขยายขนาดเนื้อหาภายในแนวตั้ง 5px แนวนอน 10px */
padding-[top,right,bottom,left]: 5px; /* ขยายขนาดมุมใดมุมนึง 5px */

border-width: 1px;                /* ปรับขอบขนาด 1px */
border-style: solid;              /* ปรับขอบเป็นแบบทีบ */
border-color: black;              /* ปรับขอบเป็นสีดำ */
border: 1px solid black;          /* Shorthand */
border-bottom: 1px solid black;   /* เพิ่มขอบเฉพาะมุมล่าง */

border-collapse: collapse;        /* ยกเลิกการเพิ่มระยะห่างขอบเนื้อหาใน <table> */
border-radius: 5px;               /* ปรับขอบมนทุกมุม 5px */
border-top-left-radius: 5px ;     /* ปรับขอบมนมุมบนซ้าย 5px */

outline: 1px solid black;         /* ปรับขอบนอกที่จะไม่กระทบกับ Element อื่นๆ */
```

## Color Value

|Code|ความหมาย|
|-|-|
|`red`|ชื่อสี|
|`#ff0000`|โค้ดสี Hex|
|`rgb(255, 0, 0)`|โค้ดสี RGB|
|`rgba(255, 0, 0, 0.5)`|โค้ดสี RGBA (โปร่งแสง)|

## Background

```css
/* กำหนดสี */
background-color: red;
background-color: #ff0000;
background-color: rgb(255, 0, 0, 0.5);

/* กำหนดรูป */
background-image: url(path/of/image.png);
background-image: url('path/of/image.png');
background-image: url("path/of/image.png");

/* การทำซ้ำ */
background-repeat: repeat;
background-repeat: no-repeat;
background-repeat: repeat-x;
background-repeat: repeat-y;

/* ตำแหน่งการวาง */
background-position: center center; /* แกน x, แกน y */
background-position: 20px 50px;
background-position-x: right;
background-position-y: bottom;

background-size: cover;         /* ขนาดพอดีจอ */
background-size: contain;       /* แสดงเต็มรูป */
background-size: 720px;         /* ขนาด 720px */

background-attachment: local;   /* คงที่เฉพาะ Element */
background-attachment: scroll;  /* เลื่อนตาม Element */
background-attachment: fixed;   /* คงที่ทั้งหมด */
```

> กำหนดพื้นหลังแบบไล่ระดับสีได้ที่ [https://cssgradient.io/](https://cssgradient.io/)

## Text

```css
color: red;           /* สีข้อความ */
text-align: center;   /* จัดข้อความกึ่งกลาง */
text-align: justify;  /* จัดข้อความพอดีหน้า */
text-indent: 2em;     /* จัดเยื้องหน้าให้กับย่อหน้า */

text-decoration-line: underline;      /* เพิ่มขีดเส้นใต้ */
text-decoration-style: wavy;          /* ปรับขีดเส้นเป็นแบบหยัก */
text-decoration-color: red;           /* ปรับสีขีดเส้นใต้ */
text-decoration: underline wavy red;  /* Shorthand */
text-decoration: none;                /* นำขีดเส้นใต้ออก */

white-space: normal;  /* ข้อความย้ายไปบรรทัดใหม่เมื่อเกินขนาด */
white-space: nowrap;  /* ข้อความแสดงบรรทัดเดียว */

word-spacing: 1em;    /* ระยะห่างระหว่างคำ */
letter-spacing: 1em;  /* ระยะห่างระหว่างอักขระ */
line-height: 1.35;    /* ความสูงของบรรทัด */
```

## Font

```css
font-size: 1em;           /* ปรับขนาดฟอนต์ */
font-style: italic;       /* เปลี่ยนฟอนต์เป็นตัวเอียง */
font-weight: bold;        /* เปลี่ยนฟอนต์เป็นตัวหนา */
font-weight: 100 ถึง 900;  /* เปลี่ยนฟอนต์เป็นขนาดต่างๆ */

/* เปลี่ยนฟอนต์ */
font-family: 'Courier New', Courier, monospace;

/* เพิ่มฟอนต์ใหม่ */
@font-face {
  font-family: "NewFont";
  src: url("path/to/font.ttf");
}
font-family: "NewFont";
```

## Shadow

```css
/* เงาข้อความ */
text-shadow: 3px 2px 5px rgb(0, 0, 0, 0.5);
text-shadow: 3px 2px 5px rgb(0, 0, 0, 0.5), -3px -2px 5px rgb(255, 0, 0, 0.5);

/* เงา Element */
box-shadow: 3px -3px 10px 3px rgb(0, 0, 0, 0.5);
box-shadow: inset 3px -3px 10px 3px rgb(0, 0, 0, 0.5);
```

## Display

```css
display: block;         /* แสดงแบบ Block */
display: inline;        /* แสดงแบบ Inline */
display: inline-block;  /* แสดงแบบผสม Inline และ Block */
display: none;          /* ไม่แสดงผล */

visibility: hidden;     /* ซ่อนการแสดงผล (ยังคงพื้นที่ไว้) */
opacity: 0.5;           /* โปร่งแสง Element */
```

## Position

```css
position: static;   /* ตำแหน่งคงที่ */
position: relative; /* ตำแหน่งตามความสัมพันธ์ของ top, right, bottom, left */
position: absolute; /* ตำแหน่งตามความสัมพันธ์สี่ทิศ และอ้างอิงตาม position: relative; ของ Element parent */
position: fixed;    /* ตำแหน่งแบบคงที่ตามความสัมพันธ์สี่ทิศ */
position: sticky;   /* ตำแหน่งแบบยึดติดเมื่อถึงความสัมพันธ์สี่ทิศ */

top: 0;       /* ทิศบน */
right: 0;     /* ทิศขวา */
bottom: 0;    /* ทิศล่าง */
left: 0;      /* ทิศซ้าย */

z-index: 199; /* ความสำคัญในแกน Z (การแสดงผลทับกับเนื้อหาอื่นๆ) */
```

```html
<!-- ตัวอย่างการใช้ position: relative; ร่วมกับ position: absolute; -->

<div style="width: 100px; height: 100px; position: relative; background: red;">
  <div style="width: 10px; height: 10px; position: absolute; background: yellow; top: 10px; right: 0;"></div>
</div>
```

## Float

```html
<img style="float: left;" src="http://via.placeholder.com/50" alt="" />
<p>Veniam minim consequat eiusmod Lorem proident adipisicing.</p>
<p>Esse nisi culpa et cupidatat laboris ex est esse fugiat nisi duis dolor mollit.</p>
```

## Flexbox

![flex-structure](https://i.imgur.com/L8s5k4z.png)

```css
display: flex; /* กำหนดเป็น Flex Container ทำให้ลูกๆเป็น Flex Item */

/* ปรับทิศทางของ Flex Item (ใช้ Property กับ Flex Container) */
flex-direction: row;            /* (ค่าเริ่มต้น) แนวนอน */
flex-direction: row-reverse;    /* แนวนอนแบบกลับด้าน */
flex-direction: column;         /* แนวตั้ง */
flex-direction: column-reverse; /* แนวตั้งแบบกลับด้าน */
```

## Flex Wrap

![flex-wrap](https://i.imgur.com/MjuSK6t.png)

```css
/* (ใช้ Property กับ Flex Container) */
flex-wrap: nowrap;          /* (ค่าเริ่มต้น) ไม่ตัดเนื้อหา */
flex-wrap: wrap;            /* ตัดเนื้อหาบรรทัดต่อไป */
flex-wrap: wrap-reverse;    /* ตัดเนื้อหาบรรทัดต่อไปแบบกลับด้าน */
```

## Flex Grow

![flex-grow](https://i.imgur.com/B5Y1J1V.png)

```css
/* ขยายขนาด Flex Item (ใช้ Property กับ Flex Item) */
flex-grow: 0;
flex-grow: 1;
flex-grow: 4;

/* ลดขนาด Flex Item (ใช้ Property กับ Flex Item) */
flex-shrink: 1;
flex-shrink: 4;
```

## Flex Justify

![justify-content](https://i.imgur.com/1Bqs3jQ.png)

```css
/* ปรับเนื้อหาตามแกนหลักของ flex-direction (ใช้ Property กับ Flex Container) */
justify-content: flex-start; /* (ค่าเริ่มต้น) */
justify-content: flex-end;
justify-content: center;
justify-content: space-between;
justify-content: space-around;
```

## Flex Align (flex-wrap: nowrap;)

![flex-align-nowrap-1](https://i.imgur.com/mUvZmeH.png)
![flex-align-nowrap-2](https://i.imgur.com/qznYHYZ.png)

```css
/* ปรับเนื้อหาตามแกนรองของ flex-direction เฉพาะ Flex Item (ใช้ Property กับ Flex Item) */
align-self: flex-start; /* (ค่าเริ่มต้น) */
align-self: flex-end;
align-self: center;
align-self: stretch;
align-self: baseline;
```

```css
/* ปรับเนื้อหาตามแกนรองของ flex-direction (ใช้ Property กับ Flex Container) */
align-items: flex-start; /* (ค่าเริ่มต้น) */
align-items: flex-end;
align-items: center;
align-items: stretch;
align-items: baseline;
```

## Flex Align (flex-wrap: wrap;)

![flex-align-wrap-1](https://i.imgur.com/0IZtfhF.png)
![flex-align-wrap-2](https://i.imgur.com/p1ys48J.png)

```css
/* ปรับเนื้อหาตามแกนรองของ flex-direction เมื่อเนื้อหาเป็นแบบ flex-wrap: warp (ใช้ Property กับ Flex Container) */
align-content: flex-start; /* (ค่าเริ่มต้น) */
align-content: flex-end;
align-content: center;
align-content: stretch;
align-content: space-between;
align-content: space-around;
```

## Transform

```css
transform: translateX(10px);        /* ย้ายไปทางขวา 10 px */
transform: translateX(-10px);       /* ย้ายไปทางซ้าย 10 px */
transform: translateY(30px);        /* ย้ายไปทางล่าง 30px */
transform: translateY(-30px);       /* ย้ายไปทางบน 30px */
transform: translate(10px, 30px);   /* ย้ายไปทางขวา 10px ล่าง 30px */

transform: scaleX(2);               /* ขยายขนาดแนวนอน 2 เท่า */
transform: scaleY(1.5);             /* ขยายขนาดแนวตั้ง 1.5 เท่า */
transform: scale(2, 1.5);           /* ขยายขนาดแนวนอน 2 เท่า แนวตั้ง 1.5 เท่า */
transform: scale(2);                /* ขยายขนาดทั้งหมด 2 เท่า */

transform: rotate(180deg);          /* หมุน 180 องศา */
transform: rotate(0.5 turn);        /* หมุนครึ่งวงกลม (เท่ากับ 180 องศา) */

transform: skew(40deg);             /* เอียงเนื้อหา 40 องศา */
```

## Time Unit

สำหรับการกำหนดเวลา

|Code|ความหมาย|
|-|-|
|`s`|วินาที|
|`ms`|มิลลิวินาที|

> `1s` = `1000ms`

## Transition

```css
transition-delay: 1s;           /* ดีเลย์ช่วงเวลาเคลื่อนไหว 1 วินาที */
transition-duration: 250ms;     /* ดำเนินการเคลื่อนไหวเป็นเวลา 0.25 วินาที */

transition-property: all;       /* ดำเนินการเคลื่อนไหวทุก Property */
transition-property: background-color transform;    /* ดำเนินการเคลื่อนไหวเฉพาะ Property background-color และ transform */

transition-timing-function: ease;       /* เคลื่อนไหวแบบค่อยๆเริ่มและค่อยๆจบ */
transition-timing-function: ease-in;    /* เคลื่อนไหวแบบค่อยๆจบขาเข้า */
transition-timing-function: ease-out;   /* เคลื่อนไหวแบบค่อยๆจบขาออก */
transition-timing-function: linear;     /* เคลื่อนไหวแบบคงที่ */
transition-timing-function: steps(4);   /* เคลื่อนไหวแบบ 4 Frames */

/* shorthand */
transition: 1s;
transition: background-color 500ms linear;
```

## Animation

```css
/* กำหนดชื่อให้กับอนิเมชั่น */
@keyframes MyAnimationName {
  from {
    background-color: red;
    border: 0;
  }
  to {
    background-color: blue;
    border: 3px solid yellow;
  }
}

.my-animation {
  animation-name: MyAnimationName;      /* เลือกใช้ keyframes */
  animation-duration: 1s;               /* ระยะเวลาเคลื่อนไหว keyframes 1 วินาที */
  animation-timing-function: linear;    /* เคลื่อนไหวแบบคงที่ */
  animation-delay: 500ms;               /* ดีเลย์ 0.5 วินาทีก่อนเคลื่อนไหว */
  animation-iteration-count: infinite;  /* ใช้ keyframes แบบวนรอบไม่จำกัด (ใช้ตัวเลขสำหรับจำกัดรอบ) */
  animation-direction: alternate;       /* เคลื่อนไหวจาก เริ่มไปจบ จากนั้น จบไปเริ่ม */
  animation-fill-mode: forwards;        /* เมื่อจบการเคลื่อนไหวให้แสดงผล keyframes สุดท้าย */
}
```

```css
/* เคลื่อนไหวแบบกำหนดเวลาด้วยเปอร์เซ็นต์ */
@keyframes name {
  0% { top: 0; left: 0; }
  30% { top: 50px; }
  68%, 72% { left: 50px; }
  100% { top: 100px; left: 100%; }
}
```

## Media Queries

```css
/* เมื่อมีขนาดหน้าจอไม่เกิน 600px */
@media screen and (max-width: 600px) {
  body {
    background-color: red;
  }
}

/* เมื่อมีขนาดหน้าจออย่างน้อย 800px เป็นต้นไป */
@media screen and (min-width: 800px) {
  body {
    background-color: blue;
  }
}

/* เมื่อมีขนาดหน้าจอระหว่าง 100px ถึง 300px */
@media screen and (min-width: 100px) and (max-width: 300px) {
  body {
    background-color: green;
  }
}

/* เมื่ออยู่โหมดพิมพ์หน้าเว็บ (Ctrl + P) */
@media print {
  body {
    background-color: violet;
  }
}
```
