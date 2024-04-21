# userscriptを書きました

### ヤフオクページを自動でリロード

```javascript
// ==UserScript==
// @name         Auto Reload Page
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  try to take over the world!
// @author       Your Name
// @match        https://auctions.yahoo.co.jp/*
// @grant        none
// @run-at       document-start
// ==/UserScript==

(function() {
    'use strict';

    setTimeout(function() {
        location.reload();
    }, 600000); // 5分ごとにページをリロード
})();

```
