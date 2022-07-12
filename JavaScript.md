### 类型

#### 内置类型

- null
- undefined
- boolean
- number
- string
- object
- symbol

我们可以用 `typeof` 运算符来查看值的类型

```javascript

typeof undefined  === "undefined"; // true
typeof true       === "boolean"; // true
typeof 42         === "number"; // true
typeof "42"       === "string"; // true
typeof { life: 42}=== "object"; // true 

typeof Symbol()   === "symbol"; // true

// null 是唯一一个用 typeof 检测会返回 object 的基本类型值
typeof null === "object";

// 可以用复合条件来判断
const a = null;
(!a && typeof a === "object"); // true

// function 实际上是 Object 的一个子类型，具体来说，函数是 “可调用对象”，它拥有一个内部属性 [[Call]]，该属性使其可以被调用
// 函数对象的 length 属性是其声明的参数的个数
typeof function a() {/*...*/} === "function"; // true

```

> Undefined 是值的一种，undeclared 则表示变量还没有声明过。

#### 类型转换

```javascript

（'b' + 'a' + + 'a' + 'a'）.toLowerCase(); // 'banana'

1 + {}; // '1[Object Object]'

{} + 1; // 1

1 + []; // '1'

```

### 值

#### 数组

#### 字符串

#### 数字

#### 

