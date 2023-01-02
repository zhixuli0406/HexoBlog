---
title: 【Hexo】如何使用Hexo架設個人部落格
date: 2023-01-02 22:48:47
tags: 
    - node.js
    - hexo
    - blog
---

# 【Hexo】如何使用Hexo架設個人部落格

- [【Hexo】如何使用Hexo架設個人部落格](#hexo如何使用hexo架設個人部落格)
  - [前言](#前言)
  - [Hexo是甚麼?](#hexo是甚麼)
  - [安裝需求](#安裝需求)
    - [Node.js](#nodejs)
    - [yarn](#yarn)
  - [Hexo環境建置](#hexo環境建置)
    - [Step1. 安裝 Hexo](#step1-安裝-hexo)

---

## 前言

前陣子突然想架設一個用來記錄技術筆記的部落格，但又不願意使用[WordPress](https://wordpress.com/zh-tw/)這種一整套的部落格 - 因為它真的太肥ㄌ(#`Д´)ﾉ。  
本來想用[Docusaurus](https://docusaurus.io/)，因為它使用了我最熟悉的React，也支援Markdown寫作，整體來說既輕量又符合我的需求。  
但是用了一陣子之後發現，Docusaurus比較適合用來撰寫開發者文件這種類型的文檔，用來當作部落格就比較沒那麼適合。  
找來找去終於讓我找到一個看起來最符合我需求的框架了，那就是本文的重點 - [Hexo](https://hexo.io/zh-tw/)。

## Hexo是甚麼?

{% blockquote Hexo官方網站 <https://hexo.io/zh-tw/> %}
A fast, simple & powerful blog framework
{% endblockquote %}

Hexo 其實就是一款基於Node.js的網誌框架，具有以下幾種特點(引用自官網介紹)：

- 超級快速： Node.js 帶給您超級快的檔案產生速度，上百個檔案只需幾秒就能建立完成。
- Markdown 支援： Hexo 支援所有 GitHub Flavored Markdown 的功能，您甚至能在 Hexo 使用大部份的 Octopress 外掛。
- 一鍵部署： 您只需要一個指令就能把網站部署到 GitHub Pages, Heroku 或其他網站。
- 豐富的外掛： Hexo 有強大的外掛系統，您可安裝外掛讓 Hexo 支援 Jade, CoffeeScript。
  
官網上的介紹狠狠的命中了我的需求。  
沒錯！我就是再找一款又輕量有能支援Markdown的網頁框架，尤其它又是使用熟悉的Node.js，根本就是為我量身打造的吧(ﾉ◕ヮ◕)ﾉ*:･ﾟ✧  
下面，就跟著我一起動手將Hexo架設起來吧！

## 安裝需求

在安裝Hexo前，我們需要在電腦中安裝一些東西：

### [Node.js](https://nodejs.org/en/)

Hexo是基於Node.js建立的網誌框架，所以我們需要安裝Node.js。這邊選擇18.12.1 LTS的版本即可。

![Node.js](/image/create-hexo-blog/node.js.png)

安裝完後我們來測試一下是否有安裝成功：

```bash
node --version
```

### [yarn](https://yarnpkg.com/)

這邊我的習慣是使用Yarn取代npm，若是習慣使用npm的朋友可以不用安裝。

```bash
npm install yarn --g
```

安裝完後照慣例，我們來測試一下是否安裝成功。

```bash
yarn --version
```

## Hexo環境建置

完成了前置作業的安裝後，接著我們就可以開始安裝Hexo了  
安裝步驟如下：

### Step1. 安裝 Hexo

![Hexo](/image/create-hexo-blog/Hexo.png)

開啟 CLI 介面（例如 cmd 等終端機），並輸入下列指令安裝 Hexo：

```bash
npm install hexo-cli -g
```

或是使用`yarn`：

> 注意：yarn並不鼓勵使用global安裝，全域安裝建議使用npm。

```bash
yarn global add hexo-cli
```

安裝完成後可輸入 hexo version 或 hexo -v 查看 Hexo 版本，確認是否有安裝成功：

```bash
hexo version
```

![HexoVersion](/image/create-hexo-blog/HexoVersion.png)
