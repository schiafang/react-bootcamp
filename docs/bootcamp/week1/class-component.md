---
title: '改用 class Component'
keywords:
  - JSX
  - React Component
---

在 React 中建立元件的方式有兩種，一種是使用函式（function）建立的，稱作 function component；另一種則是使用類別（class）來建立的，稱作 class component。

過去在 React Hooks 推出以前，function component 並不能有自己的資料狀態（state），如果 React 元件會包含有資料狀態，就得要使用 class component。但對於 JavaScript 的初學者來說，對於「類別」的概念相對陌生，因為一開始接觸 `class` 就會不太熟悉，再加上類別中的方法需要透過 `bind` 來指定 `this` 指稱到的對象，進而導致許多新手光是要建立一個 React 元件較需要先花很多時間在了解 JavaScript 這些語法。

但在 React Hooks 推出之後，透過 `useState` 這個 React Hook，開發者可以直接在 function component 中定義並使用資料狀態，因此只要對於 JavaScript 的 function 有相對的了解後，就可以開始上手 React 這套前端框架，大幅降低了學習上的難度。

```jsx
class App extends React.Component {
  constructor(props) {
    super(props);

    this.state = {
      counter: 5,
    };

    this.handleIncrease = this.handleIncrease.bind(this);
    this.handleDecrease = this.handleDecrease.bind(this);
  }

  handleIncrease() {
    this.setState(({ counter }) => ({
      counter: counter + 1,
    }));
  }

  handleDecrease() {
    this.setState(({ counter }) => ({
      counter: counter - 1,
    }));
  }

  render() {
    const { counter } = this.state;
    return (
      <div className="container">
        <div className="chevron chevron-up" onClick={this.handleIncrease}></div>
        <div className="number">{counter}</div>
        <div
          className="chevron chevron-down"
          onClick={this.handleDecrease}
        ></div>
      </div>
    );
  }
}
```
