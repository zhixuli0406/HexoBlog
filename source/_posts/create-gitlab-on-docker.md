---
title: 【Gitlab】在Docker架設Gitlab全紀錄
date: 2023-01-03 10:17:27
tags:
    - gitlab
    - docker
---

# 【Gitlab】在Docker架設Gitlab全紀錄

- [【Gitlab】在Docker架設Gitlab全紀錄](#gitlab在docker架設gitlab全紀錄)
  - [前言](#前言)
  - [GitLab是什麼?](#gitlab是什麼)
  - [為什麼要架設在Docker上?](#為什麼要架設在docker上)
  - [Install GitLab](#install-gitlab)
  - [結語](#結語)

---

## 前言

公司之前都是使用[Gitea](https://gitea.io/zh-tw/)+[Jenkins](https://www.jenkins.io/)在做版控與CI/CD，  
一開始使用上來說沒甚麼大問題，但時間久了、Repo變多之後，Gitea因為Index機制導致他越來越慢╮(╯_╰)╭  
時常因為上傳了比較大的檔案就會等很久沒有回應，甚至斷線(#`Д´)ﾉ  
久了之後受不了，只好另尋出路，  
這時候有一個很不錯的選擇擺在了我面前 - [Gitlab](https://about.gitlab.com/)

## GitLab是什麼?

[Gitlab](https://about.gitlab.com/)是由GitLab公司開發的、基於Git的整合軟體開發平台，於2011年發展至今，一直到2018年Microsoft收購了GitHub，各路開發者開始選擇(逃難)了其他的Git整合平台，其中GitLab就是開發者們選擇最多的平台。  
最初GitLab是採用 MIT 授權之免費開源軟體，現在則分為 GitLab CE（社群版）和 GitLab EE（企業版），而兩者的核心程式碼是相同的，但企業版會在核心功能之上，再疊加更多好用的進階功能。  
GitLab 提供的服務主要包含了 git 版本控制系統（version control system）、CI/CD Pipeline，以及其他專案管理的功能，像是 Wiki、Issue Tracking、Kanban、Burndown Chart⋯⋯。  
透過這些功能與工具的整合，GitLab 提供了一條龍的軟體開發 Workflow，他們將其稱之為 GitLab Workflow。

## 為什麼要架設在Docker上?

之所有選擇架設在docker上的原因很簡單 - 快速佈署與輕量化。  
GitLab有提供自家寫好的Docker Image可供佈署，也可避免各個系統上的差異導致的佈署困難。  
在災難復原的部分，Docker也比一般實體機器或VM有更短的復原時間，可使GitLab停擺的時間縮到最短。

## Install GitLab

由於GitLab官方有提供完整的Docker Image，省去了自己編寫DockerFile的工，我們可以直接使用docker run執行Docker Container，這邊選擇gitlab的CE版本：

```bash
docker run -d \
   --name gitlab \
   -p 8080:80 -p 443:443 -p 22:22 
   --privileged 
   --restart always 
   -v ~/gitlab/config:/etc/gitlab 
   -v ~/gitlab/logs:/var/log/gitlab 
   -v ~/gitlab/data:/var/opt/gitlab  
   gitlab/gitlab-ce
```

> -d : 讓容器(Container)在背景執行  
> --name : 指定容器(Container)的名稱  
> -p : 指定主端(Host)對應客端(Quest)的連接埠  
> --privileged : 容器(Container)内的 root 擁有真正的 root 權限  
> -restart : 設定為 restart，則容器在異常停止後，會自動重新啟動  
> -v : 將容器(Container)內需保存的目錄，連結至主機端的目錄(~/gitlab需替換成自己的目錄)  

稍待10分鐘後等待GitLab服務啟動，接著我們就能透過瀏覽器看看成果：

```bash
http://localhost:8080
```

![gitlab-login](/image/create-gitlab-on-docker/gitlab-login.jpg)

第一次登入我們需要取得管理者密碼：

```bash
docker exec -it gitlab grep 'Password:' /etc/gitlab/initial_root_password
```

透過取得的密碼及`root`(帳號)即可登入Gitlab管理介面，完成灑花(ﾉ◕ヮ◕)ﾉ*:･ﾟ✧。  

## 結語

先不談開發者們在因為Microsoft收購了GitHub後的逃難(?)心態，GitLab經過了10年的開發，也已經非常的完善了。  
GitLab Workflow也是闖出了很大的名聲，有很多開發者慕名而來。  
自架GitLab Server在專案管理上有很大的自由度，也不需要將程式碼放上雲端平台。  
但相對地就需要付出一定的維護成本，這部分需要審慎考慮。  
若是在於維護上有困難，也可以考慮使用GitLab官方架設好的服務 - [Gitlab.com](https://about.gitlab.com/)。  
今天教學就到這裡告一段落了，感謝大家的觀看~
