---
title: 從零開始的React
date: 2023-03-11 20:39:58
tags: javascript, typescript, npm
---

## 前置知識

在學習 React 前，建議先掌握 HTML、CSS 和基本的 JavaScript。

[從零開始的Javascript](./javascript)

[從零開始的NPM](./npm)

## React 是什麼?

React 是一個由 Facebook 開發的 JavaScript 函式庫，用於構建用戶界面。它使得開發者能夠創建可重複使用的 UI 元件，並將其與其他元件組合，從而構建複雜的用戶界面。

React 使用了一個稱為 Virtual DOM（虛擬 DOM）的技術，它使得應用程序在操作真實 DOM 時更加高效。在 React 中，當 UI 組件的狀態（state）發生變化時，React 會將新的狀態與先前的狀態進行比較，然後只更新需要更新的部分。

## 安裝 React

在使用 React 之前，需要先安裝 Node.js 環境。可以在 Node.js 官網（https://nodejs.org/）下載安裝。

安裝完成後，可以使用 Node.js 自帶的 npm（Node.js 包管理器）來安裝 React。在命令行中輸入以下命令：

```shell
npm install react react-dom
```

## 第一個 React 組件

React 中的 UI 組件是 JavaScript 函式或類別，可以返回用於渲染到頁面上的 HTML 元素。

以下是一個簡單的 React 函式組件：

```jsx
function HelloWorld(props) {
  return <div>Hello {props.name}!</div>;
}
```

這個組件可以通過將屬性傳遞給它來渲染：

```jsx
ReactDOM.render(<HelloWorld name="John" />, document.getElementById('root'));
```

在這個示例中，我們在 `ReactDOM.render` 函式中傳遞了一個組件 `<HelloWorld>` 和一個 DOM 元素作為參數，這將使組件渲染到頁面上。

當 React 遇到一個組件時，它會創建一個 React 元素，其中包含了組件的屬性和任何內部子組件。然後，React 將這些元素轉換為實際的 DOM 元素，並將其添加到頁面上。

## useState

`useState`是React提供的一個Hooks，它用於在React函數組件中添加狀態（state）。使用`useState`能夠讓函數組件也能夠擁有狀態，並且在狀態改變時重新渲染組件。

使用`useState`的步驟如下：

在函數組件中引入`useState`：

```js
import React, { useState } from 'react';
```

使用`useState`定義狀態變數以及修改狀態的函數：

```js
const [count, setCount] = useState(0);
```

上面的代碼定義了一個狀態變數count，初始值為0，以及一個修改狀態的函數`setCount`。注意，`useState`返回一個數組，第一個元素是狀態變數的初始值，第二個元素是修改狀態的函數。

使用狀態變數：

```jsx
return (
  <div>
    <p>You clicked {count} times</p>
    <button onClick={() => setCount(count + 1)}>
      Click me
    </button>
  </div>
);
```

在上面的代碼中，我們使用了狀態變數`count`，並且在點擊按鈕時調用`setCount`函數來修改狀態。

使用`useState`的好處在於能夠讓函數組件也能夠擁有狀態，並且在狀態改變時重新渲染組件。這使得我們能夠更加靈活地設計React應用程序，並且能夠更好地管理組件狀態。

## useEffect

`useEffect` 是 React Hooks 中非常重要的一個函數，可以用來處理 Component 的副作用。副作用指的是在渲染時對外部環境的讀寫操作，例如發送網絡請求、設置計時器、手動修改DOM等。 `useEffect` 的作用是讓 React 可以在渲染之後進行一些額外的操作，同時保證這些操作不會影響到渲染的結果。

使用 `useEffect` 的基本語法如下：

```jsx
import React, { useEffect } from 'react';

function MyComponent() {
  useEffect(() => {
    // 副作用操作
  });
  return <div>Component content here</div>;
}
```

在這個例子中， `useEffect` 接收一個回調函數作為參數，這個回調函數在 Component 每次渲染時都會執行。在這個回調函數中，可以進行一些副作用操作，例如發送網絡請求、設置計時器、手動修改DOM等。當然，也可以在回調函數中返回一個清除函數，這個清除函數在 Component 卸載時會自動調用，以清理副作用操作產生的資源。

```jsx
import React, { useState, useEffect } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);
  useEffect(() => {
    document.title = `You clicked ${count} times`;
    return () => {
      document.title = 'React App';
    };
  }, [count]);
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

在這個例子中，我們透過 `useEffect` 設置了一個副作用操作，當 count 狀態發生變化時，這個副作用操作會被執行。在副作用操作中，我們通過 document.title 修改了網頁標題。同時，我們也在副作用操作的返回值中定義了一個清除函數，在 Component 卸載時自動調用，將網頁標題恢復成默認值。

`useEffect` 的第二個參數可以用來限制副作用操作的執行。這個參數是一個陣列，包含了所有需要監聽的變數。當其中任意一個變數發生變化時，`useEffect`會重新執行一次並且清掉上一次的副作用

當使用 `useEffect` 時，有幾個重要的注意事項：

1. `useEffect` 的第一個參數是一個函數，它包含所有需要進行的副作用。

2. 如果第二個參數是一個空陣列，那麼這個 `useEffect` 函數只會在組件首次渲染時執行，並且不會再重新執行。

3. 如果第二個參數是一個包含了值的陣列，那麼 `useEffect` 函數只有在這些值改變時才會重新執行。

4. 如果 `useEffect` 函數返回了一個函數，那麼這個函數會在下一次重新執行或卸載時執行，進行清理操作。

## useRef

`useRef` 是 React hooks 中提供的一種 hook，主要用於保存一個可變的值，並在整個 React 组件的生命週期中保持持久性。

使用 `useRef` 前，需要先引入 `useRef`：

```jsx
import { useRef } from 'react';
```

接著，可以使用 useRef 創建一個 ref 對象：

```jsx
const ref = useRef(initialValue);
```

`initialValue` 是 ref 的初始值，可以是任何值，包括 `null`、`undefined`、數字、對象等。

`useRef` 返回一個對象，其中包含一個屬性 current，該屬性將一直持有著傳入 `useRef` 的初始值。

下面是一個簡單的範例，展示如何使用 `useRef`：

```jsx
import { useRef } from 'react';

function TextInput() {
  const inputRef = useRef(null);

  function handleClick() {
    inputRef.current.focus();
  }

  return (
    <div>
      <input type="text" ref={inputRef} />
      <button onClick={handleClick}>Focus</button>
    </div>
  );
}
```

在這個範例中，我們使用 `useRef` 創建了一個 ref 對象 inputRef，然後將這個對象傳遞給了一個 input 元素的 ref 屬性中。

在 `handleClick` 函數中，我們使用 inputRef.current 來獲取 input 元素的 DOM 對象，然後調用其 focus 方法，將焦點聚焦到 input 元素上。

這個範例展示了 `useRef` 最基本的用法，當然，`useRef` 還有更多的用途，例如：

1. 記錄上一次渲染時某個值

2. 在 `useEffect` 中保存一個不需要觸發重新渲染的變量

3. 在自定義 Hook 中保存一些內部狀態

總之，`useRef` 是一個非常有用的 React hooks，可以讓我們在 React 組件中方便地保存一些狀態，提高組件的可讀性和可維護性。

## 總結

在本文中，我們介紹了 React 的核心概念和基本使用方法，包括 JSX 語法、元件、狀態管理等。並且講解了 `useState`、`useEffect` 和 `useRef` 這些常用的 React Hook，以及如何使用它們來進行狀態管理和資料讀寫等操作。

React 是一個非常強大且受歡迎的前端框架，它提供了豐富的生態系統和廣泛的應用場景。學習 React 可以讓開發者更高效地開發出複雜的前端應用程式，也能夠提升開發效率和程式品質。

希望本文能夠對初學者有所幫助，讓大家更快地上手 React 的學習，並且能夠應用到實際開發中。
