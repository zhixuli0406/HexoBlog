---
title: 【React新手入門 - 01】什麼是React？
date: 2023-01-14 22:47:11
tags:
    - React
---

# 【React新手入門 - 01】什麼是React？

- [【React新手入門 - 01】什麼是React？](#react新手入門---01什麼是react)
  - [React是甚麼？我真的需要它嗎？](#react是甚麼我真的需要它嗎)
  - [開始React的旅程](#開始react的旅程)
    - [安裝Node.js與npm](#安裝nodejs與npm)
    - [安裝yarn](#安裝yarn)
    - [安裝create-react-app](#安裝create-react-app)
  - [結語](#結語)

---

## React是甚麼？我真的需要它嗎？

首先，我們要先知道框架(Framework)是什麼？  
隨著近代網頁功能越來越多、網頁的架構越來越大，我們需要的`<script>`標籤也越來越多，越來越多重複的程式碼散落在各個html檔中，這導致建構與維護越來越複雜。  
終於有一天，工程師們受不了了，心想：既然平常也都是使用`javascript`去處理`css`和`html`，那為什麼不也用`javascript`去處理所有事情呢？  
於是，各家工程師就開始研發處理這個問題的`javascript`，並將這些程式碼統合成一個個函式庫，這些函式庫就稱為框架(framework)。

最一開始孕育而生的是像`jquery`、`Extjs`等函式庫，但由於它們均是直接操作實體DOM(Document Object Model)，導致有些時候效能會比較差，且會比較容易出現預期之外結果的情況。  
為了解決這些問題，工程師們又再努力研發(爆肝?)，終於提出一項突破性的技術 - Virtual DOM(虛擬DOM)。

使用這項技術的框架中，又以Google寫的Angular、中國人寫的Vue、和Facebook寫的React，這三大框架最有名。  
這三大框架也被稱為「前端框架三本柱(三幻獸？)」。

然而，瀏覽器不可能平白無故的認得各家自己寫的函式庫，尤其各家研發出來的函式庫使用規則五花八門，不可能讓各個瀏覽器都支援。  
因此，我們網頁開發流程從原本的：

> 1. 編寫程式碼
> 2. 輸出網頁程式(html、css......)
> 3. 透過瀏覽器呈現

變成：

> 1. 載入函式庫
> 2. 編寫程式碼
> 3. 將新語法/函式庫「編譯及打包」成瀏覽器能讀懂的程式碼
> 4. 輸出程式碼
> 5. 透過瀏覽器呈現

因此我們也需要下列工具協助我們打包及編譯：

1. 套件管理工具(ex: npm/yarn)
2. 打包工具(ex: webpack)
3. 編譯器(ex: babel)

講到這裡，你可能會覺得：使用框架也沒比較簡單啊，還是一樣很麻煩！  
但框架的優點在於我們只需要專注於撰寫程式碼，不用去考慮複雜的操作，也可以節省掉很多重複的程式碼，提高程式碼的可讀性與減少維護成本。
所以到底需不需要使用框架？我覺得在網站功能較多、較複雜的情況下使用框架是一件省時省力的事情。但殺雞焉用牛刀，請依專案大小及複雜度來評估自己需不需要使用到框架。

## 開始React的旅程

在開始寫React之前，我們需要先安裝一些工具來協助我們開發。

### 安裝[Node.js](https://nodejs.org/en/)與npm

npm是「套件管理工具」，簡單來說就是一個可以把寫好的程式碼打包放在上面讓人使用的平台。  
前面有提到React是Facebook寫好的函式庫，代表我們可以透過npm安裝使用。

我們需要安裝Node.js，npm會跟著Node.js一起安裝。這邊選擇18.12.1 LTS的版本即可。

![Node.js](/image/create-hexo-blog/node.js.png)

安裝完後我們來測試一下是否有安裝成功：

```bash
node --version
```

### 安裝[yarn](https://yarnpkg.com/)

這邊我的習慣是使用yarn取代npm，若是習慣使用npm的朋友可以不用安裝。

```bash
npm install yarn --g
```

安裝完後照慣例，我們來測試一下是否安裝成功。

```bash
yarn --version
```

### 安裝[create-react-app](https://create-react-app.dev/)

React官方有在npm上提供我們已經設定好webpack(打包工具)、babel(編譯器)和react的範本程式。  
可以直接使用create-react-app召喚(?)出已經設定好所有東西的「腳手架」(Scaffolding)，讓我們節省很多設定的動作。  
這邊直接使用npm安裝即可。

```bash
npm install -g create-react-app
```

## 結語

到這邊，我們認識了React，也安裝完開發React所需的相關套件，下一章將開始介紹怎麼使用create-react-app來開始我們第一個React專案。
