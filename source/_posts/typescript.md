---
title: 從零開始的Typescript
date: 2023-03-13 17:07:32
tags: javascript, typescript
---

如果您想要開始學習 TypeScript，請確保您已經具備以下環境：

1. JavaScript 知識: [從零開始的Javascript](./javascript)
2. Node.js 環境與 npm 套件管理系統: [從零開始的NPM](./npm)

以下是一個從零開始學習 TypeScript 的步驟：

## 安裝 TypeScript

首先，您需要在電腦上安裝 TypeScript。您可以使用以下 npm 命令進行安裝：

```shell
npm install -g typescript
```

## 創建 TypeScript 檔案

接下來，讓我們創建一個 TypeScript 檔案。假設我們要創建一個名為 hello.ts 的檔案。

1. 在您想要創建 TypeScript 檔案的目錄中，創建一個名為 hello.ts 的檔案。

2. 在 hello.ts 檔案中，輸入以下程式碼：

```ts
function sayHello(name: string) {
  console.log(`Hello, ${name}!`);
}

const myName: string = "TypeScript";
sayHello(myName);
```

這裡，我們創建了一個 `sayHello` 函數，它將一個名稱作為引數並輸出 `Hello, {name}!` 字串。接著，我們創建了一個 `myName` 變數，它是一個字串型別並被賦值為 "TypeScript"。最後，我們呼叫了 `sayHello` 函數並傳遞 `myName` 作為引數。

## 編譯 TypeScript 檔案

接下來，我們需要將 TypeScript 檔案編譯成 JavaScript 檔案。

1. 在命令列中，切換到 hello.ts 檔案所在的目錄。

2. 輸入以下命令以編譯 TypeScript 檔案：

```shell
tsc hello.ts
```

這將會使用 TypeScript 編譯器編譯 hello.ts 檔案並產生一個名為 hello.js 的 JavaScript 檔案。

## 執行 JavaScript 檔案

現在，我們已經將 TypeScript 檔案編譯成 JavaScript 檔案。接下來，讓我們執行 hello.js 檔案。

```shell
node hello.js
```

這將會執行 `hello.js` 檔案並輸出 Hello, TypeScript! 字串。

## TypeScript基本語法

### 變數宣告

在TypeScript中，可以使用`let`和`const`聲明變數，用法和JavaScript一樣。不同之處在於，TypeScript會根據變數的初始值來推斷變數的類型。如果變數沒有初始值，則需要指定變數的類型。

```ts
let a: number = 1;
const b: string = "hello";
let c = true; // TypeScript會自動推斷c的類型為boolean
let d; // TypeScript無法推斷d的類型，需要手動指定
```

### 函數宣告

在TypeScript中，可以使用function關鍵字聲明函數。需要指定函數的參數類型和返回值類型。

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

如果函數沒有返回值，可以指定返回值類型為`void`。

```ts
function log(message: string): void {
  console.log(message);
}
```

### 介面

在TypeScript中，可以使用介面來定義物件的形狀。介面定義了物件的屬性和方法，但沒有具體的實現。

```ts
interface Person {
  name: string;
  age: number;
  sayHello(): void;
}
```

使用介面來聲明一個物件時，需要符合介面的形狀。

```ts
let person: Person = {
  name: "Tom",
  age: 18,
  sayHello: function () {
    console.log("Hello, my name is " + this.name);
  },
};
```

### 類

在TypeScript中，可以使用類來創建物件。類是一個模板，用來創建具有相同屬性和方法的物件。

```ts
class Animal {
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  sayHello() {
    console.log("Hello, my name is " + this.name);
  }
}
```

使用類來創建一個物件時，需要使用new關鍵字。

```ts
let dog = new Animal("Dog");
dog.sayHello(); // Hello, my name is Dog
```

## 泛型

### 什麼是泛型？

泛型（Generics）是指在定義函式、介面或類別時，不指定特定的型別，而是使用一個參數來表示型別，使得這些定義能夠支援多種型別。通過泛型，我們可以寫出更加通用、靈活的程式碼。

例如，我們定義一個函式 `identity`，該函式返回傳入的值：

```ts
function identity(value: any): any {
  return value;
}
```

這個函式看似沒有問題，但是它的參數型別和返回值型別都是 any，這意味著我們不能獲取到這個值的任何有用資訊。因此，我們需要使用泛型來指定型別。

### 使用泛型

在 TypeScript 中，可以使用 `<T>` 來表示泛型型別參數，其中 T 可以是任意名稱，表示任意型別。例如，我們可以將上面的 `identity` 函式改寫為泛型函式：

```ts
function identity<T>(value: T): T {
  return value;
}
```

這樣，我們就可以在調用 `identity` 函式時指定其返回值的型別：

```ts
let result = identity<string>('Hello, world!');
```

在這個例子中，我們將泛型參數 T 指定為 `string`，表示 `identity` 函式返回的值的型別為 `string`。因此，變數 `result` 的型別也是 `string`。

### 泛型類別

除了泛型函式外，我們還可以使用泛型來定義類別。例如，下面是一個使用泛型的 `Pair` 類別：

```ts
class Pair<T, U> {
  constructor(public first: T, public second: U) {}
}
```

這個類別可以用來表示兩個值的組合。其中的 `T` 和 `U` 分別表示第一個值和第二個值的型別。我們可以在創建對象時指定這兩個型別：

```ts
let pair = new Pair<number, string>(1, 'hello');
```

在這個例子中，我們將 `T` 指定為 number，`U` 指定為 string，表示 pair 對象的第一個值的型別為 number，第二個值的型別為 string。

## 枚舉(Enum)

枚舉（Enum）是 `TypeScript` 中的一種數據類型，用於定義一些具有名字的常量集合。枚舉類型通過列舉所有可能的值來限制變量的取值範圍，從而增強程序的可讀性和可維護性。

在 `TypeScript` 中，使用關鍵字 `enum` 來定義枚舉類型。以下是一個示例：

```ts
enum Color {
  Red,
  Green,
  Blue,
}
```

上面的程式碼定義了一個名為 `Color` 的枚舉類型，其中包含了三個可能的取值 Red、Green 和 Blue。默認情況下，枚舉類型的值從 0 開始依次遞增，所以 Red 的值為 0，Green 的值為 1，Blue 的值為 2。

除了默認的數字值外，枚舉類型還可以手動賦值。以下是一個手動賦值的示例：

```ts
enum Color {
  Red = 1,
  Green = 2,
  Blue = 4,
}
```

上面的程式碼中，枚舉值 Red 被手動賦值為 1，Green 被賦值為 2，Blue 被賦值為 4。這里手動賦值的好處是可以保證每個枚舉值的取值唯一性，避免了可能出現的錯誤。

枚舉類型可以作為函數參數和返回值的類型，也可以作為類的屬性類型。以下是一個枚舉作為類屬性類型的示例：

```ts
enum Color {
  Red = 1,
  Green = 2,
  Blue = 4,
}

class Car {
  color: Color;

  constructor(color: Color) {
    this.color = color;
  }
}

const myCar = new Car(Color.Green);
console.log(myCar.color); // 输出 2
```

在上面的程式碼中，`Car` 類中的 color 屬性的類型被定義為 Color 枚舉類型。在創建 `myCar` 實例時，我們將枚舉值 Green 作為參數傳遞給構造函數，從而將車的顏色設置為綠色。

總的來說，枚舉類型是 `TypeScript` 中非常實用的一種數據類型，可以使程式更易讀、易維護，減少程式碼中的錯誤和冗余。

## 總結

`TypeScript` 是一種靜態型別的程式語言，它是 `JavaScript` 的超集合，增加了強大的型別系統，使得程式碼更加健壯且易於維護。

總體來說，`TypeScript` 的學習曲線相對於 `JavaScript` 來說較為陡峭，但學習 `TypeScript` 可以使得我們開發出更加健壯、可靠的前端應用。
