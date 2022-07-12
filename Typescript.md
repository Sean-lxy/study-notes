### TypeScript 项目构成 



### 类型系统

#### 接口

在面向对象语言中，接口是对行为的抽象，而具体如何行动需要由类去实现。

`TypeScript` 中的接口是一个非常灵活的概念，除了可用于对于类的一部分行为进行抽象以外，也常用于对 `对象的形状` 进行描述。

```typescript

// 内联形式
declare const list: { name: string, readonly id: number };

interface List {
  name： string;
  // 只读属性
  // 只读的约束存在于第一次给对象赋值的时候，而不是第一次给只读属性赋值的时候。
  readonly id； number;
  // 任意属性
  [x: string]: any
  // 可选属性
  age?: number
}

interface Result {
  data: List[]
}

function render(result: Result) {
  result.data.forEach((value) => {
    console.log("value", value.id, value.name);
  })
};

// 类型断言
render(<Result>{
  id: '3',
  name: '321'
});

render({
  id: '3',
  name: '123'
} as Result);

// 混合接口
interface Lib {
  (): void;
  version: string;
  doSomething(): void;
}

const lib: Lib = (() => {}) as Lib;
lib.version = '1.0';
lib.doSomething = () => {};

```



#### 泛型





#### 介绍

##### TypeScript中的数据类型

- Boolean
- Number
- String
- Array
- Function
- Object
- Symbol
- undefined
- null
- `void`
- `any`
- `never`
- `元组`
- `枚举`
- `高级类型`



#### 基本类型

```typescript
// 原始类型
const bool: boolean = true;
// number
const num: number = 321;
// 二进制表示法
const binaryLiteral: number = 0b1010;
// 八进制表示法
const octalLiteral: number = 0o744;
const notANumber: number = NaN;
const infinityNumber: number = Infinity;

const str: string = 'abc';

// 元组
// 限定了类型与长度的特殊数组
// 允许push新元素，不能访问越界的元素const tuple: [number, string] = [0, '1'];


// 对象
const obj: {x: number, y: number} = {x: 1, y: 2};

// symbol
const s1: symbol = Symbol();

// undefined， null
// null 和 undefined 是所有类型的子类型
// 关闭 strictNullCheck 时，null 与 undefined 可以赋值给其他类型
const un: undefined = undefined;
const nu: null = null;

// void
// 没有任何返回值的类型
const noReturn = () => {};

// any
//任意类型
let x;
x = '123';
x = 456;

// never
// 永远不会有返回值的类型
let noError = () => throw new Error('error');

```



#### 枚举类型

具有名字的常量集合

```typescript
// 数字枚举
// 可自定义初始值
enum Role {
  Reporter = 1,
  Developer,
  Maintainer,
  Owner,
  Guest,
}

// 是通过反向映射的方法实现
var Role;
(function (Role) {
  Role[Role["Reporter"] = 1] = "Reporter";
  Role[Role["Developer"] = 2] = "Developer";
  Role[Role["Maintainer"] = 3] = "Maintainer";
  Role[Role["Owner"] = 4] = "Owner";
  Role[Role["Guest"] = 5] = "Guest";
})(Role || Role = {});

// 字符串枚举
enum Message {
  Success = "Succeed",
  Fail = "Failed"
}

// 常量枚举
const enum Month {
  Jan
  Feb
  Mar
}

```

#### 联合类型

Union Types 表示取值可以为多种类型中的一种，只能访问此联合类型的所有类型中共有的属性或方法。

```typescript

let favoriteNumber: string | number;

favoriteNumber = 123;
favoriteNumber = 'abc';

```

#### 数组类型

```typescript

// 数组类型
const array1: number[] = [1, 2, 3];

// 数组泛型
const array2: Array<number> = [1, 2, 3];
// Array 是内置的泛型接口
const array3: Array<number | string> = [1, 2, '3'];

// 用接口的形式
interface NumberArray {
  [index: number]: number;
}
let fibonacci: NumberArray = [1, 1, 2, 3, 5];

// 类数组
// 常用的类数组都有自己的接口定义，如 IArguments， NodeList， HTMLCollection
```



#### 函数的类型

```typescript

// 函数

// 可选参数后面不允许再出现必选参数
const add = (x: number, y: number = 2, c?: string): number => x + y;

// 定义函数类型
let compute = (x: number, y: number) => number;
compute = (a, b) => a + b;
// 接口形式
interface Add {
  (x: number, y: number): number
}
// 类型别名
type Add = (x: number, y: number) => number

const add: Add = (a, b) => a + b;

// 重载
function reverse(x: number): number
function reverse(x: string): string
function reverse(x: number | string): number | string | void {
  if (typeof x === 'number') {
        return Number(x.toString().split('').reverse().join(''));
    } else if (typeof x === 'string') {
        return x.split('').reverse().join('');
    }
}

```

#### 接口 Interface

类型断言

Type Assertion 可以用来手动指定一个值的类型

```typescript

// 语法
值 as 类型

// 用途
// 1. 将联合类型断言为其中一个类型

// 2. 将一个父类断言为更加具体的子类

// 3. 将任何一个类型断言为any

// 4. 将any断言为一个具体的类型

```



#### 类型别名

#### 泛型

把明确类型的工作推迟到创建对象或者调用方法的时候才去明确的特殊的类型。

简单来说：把类型当做参数一样去传递。

#### 类

1. 继承

2. 静态（static）：静态属性会被所有的实例共享

3. 访问修饰符：public、protected、private

4. 抽象（abstract）：

   - abstract类不能被实例化，用户必须创建一个类来继承abstract
   - abstract成员不能直接被访问，子类必须实现这个功能

5. 构造器（constructor）

6. 属性初始化：ES7

7. __extends

   ```javascript
   
   // d表示派生类，b表示基类
   var __extends = this.__extends || function(d, b) {
     // 1. 将基类的静态成员复制到子类
     for (var p in b) {
       if (b.hasOwnProperty(p)) {
         d[p] = b[p];
       }
     }
       
     function __() {this.constructor = d;}
     
     __.prototype = b.prototype;
     d.prototype = new __();
     
     // or 
     d.prototype.__proto__ = b.prototype;
   }
   
   ```

   

