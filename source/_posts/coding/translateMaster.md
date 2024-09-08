---
title: 路見不平，拔刀翻譯。Docusaurus 框架下的文檔翻譯
date: 2024-08-30 09:10:04
tags:
  - project
categories: [coding]
---

今天要來翻譯 Docusaurus 文檔，首先先介紹一下什麼是 [Docusaurus](https://github.com/facebook/docusaurus) 。
<!-- more -->
> 要實作這篇文章的內容需要事先安裝 node.js，這邊假設大家都有環境

## 什麼是 Docusaurus？
![alt text](/images/coding/Docusaurus.png)

Docusaurus 是由 Facebook（現為 Meta）在 2017 年推出的一個專門用於建立靜態網站的開源框架，尤其適合用來創建文檔網站，當然 Docusaurus 也可以拿來當作自己的文字部落格框架，省去刻網頁的麻煩。這個框架廣泛應用於各種技術文檔和產品說明書，像是 Unity Style Guide、React Native 或是中電會的文檔都有使用。點[這裡](https://github.com/facebook/docusaurus/network/dependents)可以看到使用 Docusaurus 的開源 repo，如果想貢獻開源力或練習英文閱讀可以到這裡尋找目標。


Docusaurus 支援 i18n（國際化），這使得網站能夠支持多種語言。這對於希望拓展全球市場的公司、開發者、和看到英文就想關掉的人來說尤其重要。我們只要在 i18n 資料夾下放置我們翻譯好的內容就可以在前端輕鬆切換語言。

## 設定翻譯文件
我這次找的文檔是 Overture Maps 的文檔，它現在是沒有 i18n 資料夾的，但因為我們很確定它使用 Docusaurus 框架，所以我們可以直接跟著[官方文檔](https://docusaurus.io/docs/i18n/tutorial)走，先使用下面這條命令產生資料夾。
```bash
npx docusaurus write-translations --locale zh-Hant
#語言要改成你要翻譯的語言，這裡是正體中文
```

接著在 ```docusaurus.config.js```設定該語言的資訊和啟用多語言選單，

```js
export default {
  i18n: {
    defaultLocale: 'en',
    locales: ['en', 'fr', 'fa'],
    localeConfigs: {
      en: {
        htmlLang: 'en-GB',
      },
      'zh-Hant': {
        label: '繁體中文', 
        direction: 'ltr', 
      }
    },
  },
  ...
  navbar: {
      items: [
        // 其他 nav 設定
        {
          type: 'localeDropdown', // 切換語言按鈕
          position: 'right',
        },
      ],
    },
};
```

開啟切換語言按鈕後就會在網頁右上角看到它了，真棒！
![alt text](/images/coding/transDemo.png)


上面都設定好之後我們到專案根目錄底下應該會看到 i18n 和準備翻譯語言的資料夾zh-Hant，Docusaurus 有一些內建的選單或錯誤頁面會用 JSON 先幫我們翻譯好，大概看過沒問題就可以不用管它了，我們要看的是 ```docusaurus-plugin-content-docs/current ``` 裡面的 mdx 或 markdown 檔案，這些就是真正要翻譯的網站內容，最後就是精神時光屋的部分了，這邊不教英文，希望大家都能為開源社區盡一份力。

![alt text](/images/coding/zh-HantFloder.png)

這樣，你就可以說你參與過百人專案了。