### 1. let 和 const

#### let 命令

存在变量提升：声明的变量一定要在声明后使用，否则会报错

暂时性死区（temporal dead zone，简称 TDZ）

```javascript
var tmp = 123;

if (true) {
	tmp = 'abc'; // ReferenceError
	let tmp;
}
```

> ES6明确规定，如果区块中存在 `let` 和 `const` 命令，这个区块对这些命令声明的变量，从一开始就形成了封闭作用域。凡是在声明之前使用这些变量，就会报错。

不允许重复声明：不允许在相同的作用域内，重复声明同一个变量

#### 块级作用域

- 函数只能在顶层作用域和函数作用域之中声明，不能在块级作用域声明。
- ES6 的块级作用域必须有大括号，没有大括号引擎就认为不存在块级作用域。

#### const 命令

const 用于声明常量，一旦声明，值就不能改变。

- 一旦声明变量，就必须立即初始化，不能留到以后赋值。
- 本质上是变量指向的那个内存地址所保存的数据不得改动。

如果想要冻结对象，应该使用 `Object.freeze` 方法

```javascript
var constantize = (obj) => {
	Object.freeze(obj);
	Object.keys(obj).forEach((key, i) => {
		if (typeof obj[key] === 'object') {
			constantize(obj[key]);
		}
	})
}
```

> - ES5 中只有两种声明变量的方法：`var` 和  `function` 命令。ES6除了添加 `let` 和  `const`  命令，还有 `import` 命令和 `class`  命令。所以一共有 6 种声明变量的方法。
>
> - `var` 与  `function`  声明的全局变量依旧是顶层对象的属性，`let `、`const` 、`class` 命令声明的全局变量不属于顶层对象的属性。
> - `ES2020` 引入了 `globalThis` 作为顶层对象。

### 2. 解构赋值

#### 数组的解构赋值

#### 对象的解构赋值

#### 字符串的解构赋值

#### 数值和布尔值的解构赋值

#### 函数参数的解构赋值

### 3. 字符串的扩展



### 4. 正则的扩展



### 5. 数值的扩展



### 6. 函数的扩展



### 7. 数组的扩展



### 8. 对象的扩展

#### 使用 `Object.assign` 扩展对象

`Object.assign` 函数会改变它的第一个参数。参数格式是 `(target, ...sources)` 。每个源对象都会应用到目标对象上，源对象依次应用，源对象的属性依次应用。

最好每次调用 `Object.assign` 时都传入一个全新的对象作为第一个参数。

`Object.assign` 只会遍历自身可数的属性，其中包括字符串和 Symbol 属性。

#### 使用 `Object.is` 进行对象比较

大部分情况下，`Object.is(a, b)` 与` a === b` 等价。但是有两种情况不同：NaN; -0 和 +0；

```javascript

NaN === NaN  // false

Object.is(NaN, NaN) // true

+0 === -0 // true

Object.is(+0, -0) // false

```

#### `Object.setPrototypeOf`

设置一个对象的原型引用为另一个对象

### 9. Symbol

Symbol 有三种类型，每种类型是用不同方式访问的：

####  本地 Symbol

通过内置 Symbol 包装对象创建，并通过存储引用或反射来访问。

Symbol 的属性无法通过 `for ... in`、 `Object.keys`、`Object.getOwnPropertyNames` 获取。只能使用 `Object.getOwnPropertySymbols` 来获取。

```javascript

const symbol = Symbol('my Symbol');

const secondSymbol = Symbol('my Symbol');

symbol === secondSymbol; // false

typeof symbol; // "symbol"

```

#### 全局 Symbol

通过另一种API 创建，跨代码域共享；

访问运行环境下的全局 Symbol 注册表：`Symbol.for` 和 `Symbol.keyFor`

```javascript

// Symbol.for(key) 可以用来查找运行环境下的全局Symbol注册表中的key值。存在则返回，否则则注册一个新的。
// 因为会将 key 作为 Symbol 的描述，所以最好给 Symbol 的key添加前缀。
const example = Symbol.for('example');

example === Symbol.for('example'); // true

// Symbol.keyFor(symbol) 能够返回一个Symbol类型的 Symbol 在添加到全局注册表时所关联的 key 值。

Symbol.keyFor(example); // example


```

####  通用 Symbol

内置于 JavaScript 中，能够在不破坏现有代码的情况下扩展语言

- Symbol.toPrimitive：可以将一个函数赋给它，该函数将决定对象如何转换成基本值
- Symbol.match：如果将一个正则表达式的 Symbol.match 属性设为false，当传入`.startsWith`、`.endsWith`、`.includes` 时，该正则表达式会将被当作字符串字面量。
- Symbol.iterator：在任意对象上使用该符号定义一个函数可以在不同的语言结构上迭代序列。



#### Symbol 的实际用法

- 将对象映射到 `DOM` 元素
- 自定义序列化行为
- 在任意两个代码作用域共享（如ServiceWorker 和 Web 页面）

### 10.  Set 和 Map 结构



### 11. Proxy 与 Reflect



#### 代理捕获器

1. `has` 
2. `deleteProperty` 
3. `defineProperty`
4. `ownKeys` 
5. `getOwnPropertyDescriptor`
6. `apply`
7. `construct`
8. `getPrototypeOf`
9. `setPrototypeOf`
10. `preventExtensions`
11. `isExtensible`
12. 

### 12. Promise



### 13. Iterator



### 14. Generator



### 15. Decorator

JavaScript 装饰器可以应用于类以及任何静态定义的属性，如对象字面量或类声明中的属性，包括 `get/set` 存取器或 `static` 属性。

