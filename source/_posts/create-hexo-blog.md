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
    - [安裝 Hexo](#安裝-hexo)
    - [初始化 Hexo](#初始化-hexo)
    - [安裝相依性檔案](#安裝相依性檔案)
      - [\_config.yml](#_configyml)
      - [package.json](#packagejson)
      - [scaffolds 模板](#scaffolds-模板)
      - [source 資源](#source-資源)
      - [themes 主題](#themes-主題)
    - [常用指令](#常用指令)
      - [新增文章](#新增文章)
      - [清除快取](#清除快取)
      - [啟動伺服器](#啟動伺服器)
  - [結語](#結語)

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

### 安裝 Hexo

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

### 初始化 Hexo

接著要初始化 Hexo，請使用下列指令初始化 Hexo：

```bash
hexo init <資料夾名稱>
```

直接執行此命令會自動於所在目錄建立一個新資料夾用來儲存 Hexo。  
記得將括號內修改成自己的資料夾名稱，若不指定資料夾名稱，則會直接初始化當前目錄。

### 安裝相依性檔案

初始化成功後，請進入初始化時創建的資料夾：

```bash
cd <資料夾名稱>
```

> 也可以直接在資料夾目錄輸入 cmd，按下 enter 後就會在這個路徑開啟終端機。

執行`yarn`安裝所需套件：

```bash
yarn
```

或是使用`npm`進行安裝：

```bash
npm install
```

安裝完成後會看到下列目錄及檔案：

```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

#### _config.yml

- 紀錄有關網站相關配置設定，可自行修改各種配置內容。例如：網站標題、使用主題名稱等等。
- 相關配置詳細說明可參考[官方文件](https://hexo.io/zh-tw/docs/configuration)

#### package.json

- 記錄所有應用程式相關配置與網站需要的所有模組。

#### scaffolds 模板

- 網站版模存放位置，當新建新文章時，Hexo會依據 scaffolds 中的版模新增相應的檔案。
- 資料夾中有三種預設佈局 - post、page 和 draft，分別對應：要發布的文章、頁面、草稿。

#### source 資源

- 用來存放原始檔案的地方，例如 Markdown、圖片、各種頁面（分頁、關於等）。
- Markdown 檔和 HTML 檔會被解析，並放到 public 資料夾，而其他檔案則會被拷貝過去。

#### themes 主題

- 用來放置網站主題的資料夾
- Hexo 會根據主題來解析 scouce 資料夾中的檔案並產生靜態頁面。

### 常用指令

接下來介紹操作Hexo比較常用到的指令語法，更多詳細指令可參考[官方文件](https://hexo.io/zh-tw/docs/commands)：

#### 新增文章

```bash
hexo new [layout] <title>
```

- 如果沒有設定 layout，則會使用 _config.yml 中的 default_layout 來設定。
- 如果title中含有空格，需使用引號框住，例如 `" title"`。
- 檔案名稱盡量以英文命名，避免出現亂碼。

#### 清除快取

```bash
hexo clean
```

用來清除產生的快取（db.json）與靜態文件 (public)。

#### 啟動伺服器

```bash
hexo server
```

- 在本地端啟動 Hexo 伺服器，預設路徑為：http://localhost:4000/。
- 可以用來預覽編輯，在部屬前先查看結果，使用 CTRL + C 可關閉。

## 結語

Hexo是一款非常輕量化的部落格框架，官方也提供很多Plugin與主題可以使用，適合熟悉Markdown語法的工程師用來記錄技術相關文章。
非常推薦不想使用 WordPress 的大家來嘗試看看！
