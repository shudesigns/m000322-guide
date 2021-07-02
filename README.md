＊bootstrap版本：  
我CSS用的是bootstrap 5.0，純粹是覺得5.0的網格系統比較好用；用到一半才發現bootstrap-select不支援5.0的js，所以變成是「CSS版本為5.0，js版本為4.5」，目前用下來基本上沒什麼問題

### 【樣式】

第一階段大部分的設計都是之前他們找的設計公司做的～那時候的設計稿有很詳細的設計規範，所以我直接拿來用（不過後來Mia似乎沒有完全照著用~XD所以還是以設計稿為主）

基本樣式的變數我都寫在/styles/sass/config/_bootstrap-variables.scss
下面做補充說明，看不懂可以問我～

```sass
$giant-blue
// 巨大集團的品牌主色，基本上官網的藍色都是這個顏色

$blue-1, $blue-2, $blue-3`  
// 最初的設計稿有特別標示這些輔助色，不過後來用到的機會很少，參考就好

$body-color, $dark
// 文字基本色

$gray-1, $gray-2 
// 當初設計稿上指定文字用的灰色，參考就好

$stock-green, $stock-red
// 股價標示用的綠色和紅色

$bg-gray, $bg-line-gray
// 背景的灰色和背景線條的灰色

$giant, $liv, $momentum, $cadex
// 四個品牌的主色，這邊的$giant是捷安特不是巨大集團，顏色不一樣!!

$grid-breakpoints
// 螢幕寬度的主要斷點

$container-max-widths
// .container的最大寬度，當初設計稿是分成「桌機、平板橫放、平板直放、手機」四種情況去做RWD，不過我想Mia沒有照著用，所以參考就好
```

### 【版面】

header跟banner是比較討厭的地方...  
我有針對目前出現過的幾種設計做不同的設定，有問題可以再問我

#### A. banner滿版+導覽列在下方
這個版型的設計是「手機版(576px)以上都是滿版，導覽列在banner下方；手機版為橫式，導覽列在banner上方」（不要問我，當初的設計稿就是這樣~QQ），所以banner背景圖有分橫式和直式兩種  
（參考頁面：[http://html.m000322.24241872.tw/vision](http://html.m000322.24241872.tw/vision)）
```html
<div class="page-top default has-nav">
  <div class="page-hero full-screen">
    <div class="page-hero-bg pic-fill imgFill">
      <picture>
        <source media="(orientation: portrait)" srcset="/styles/images/about/hero-portrait.jpg" /><!-- 1024 * 1200 px -->
        <img src="/styles/images/about/hero.jpg" alt="" /><!-- 1920 * 600 px -->
      </picture>
    </div><!-- // page-hero-bg -->
    <div class="page-hero-inner container">
      <div class="page-hero-content text-white" data-aos="fade-down">
        <h1 class="title fw-700 lh-125 mb-0">推動自行車世界的進化</h1>
        <p class="summary fw-300 mt-4 mb-0 lh-175 ls-0025">我們整合整個產業價值鏈和全球業務，使我們能夠以無與倫比的合作方式提供相關合作夥伴更寬廣的創新和發展機會。</p>
      </div>
    </div><!-- // page-hero-inner -->
  </div><!-- // page-hero -->
  <div class="page-nav">
    <div class="page-nav-inner container">
      <div class="page-nav-swiper swiper-container">
        <div class="swiper-wrapper">
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/vision" data-sub-category="info">集團簡介</a></div>
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/group" data-sub-category="management">集團經營與管理</a></div>
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/footprint" data-sub-category="footprint">全球版圖</a></div>
        </div>
      </div><!-- // page-nav-swiper -->
    </div><!-- // page-nav-inner -->
  </div><!-- // page-nav -->
</div><!-- // page-top -->
```

#### B. 沒有banner圖片，只有導覽列
單純只有導覽列  
（參考：[http://html.m000322.24241872.tw/footprint](http://html.m000322.24241872.tw/footprint)）
```html
<div class="page-top default has-nav">
  <div class="page-nav">
    <div class="page-nav-inner container">
      <div class="page-nav-swiper swiper-container">
        <div class="swiper-wrapper">
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/vision" data-sub-category="info">集團簡介</a></div>
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/group" data-sub-category="management">集團經營與管理</a></div>
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/footprint" data-sub-category="footprint">全球版圖</a></div>
        </div>
      </div><!-- // page-nav-swiper -->
    </div><!-- // page-nav-inner -->
  </div><!-- // page-nav -->
</div><!-- // page-top -->
```

#### C. 最新消息（Banner非滿版，導覽列在下方）
基本上算是A的變化型，單純只有橫式
（參考：[http://html.m000322.24241872.tw/news](http://html.m000322.24241872.tw/news)）
```html
<div class="page-top default has-nav news-top">
  <div class="page-hero">
    <div class="page-hero-bg pic-fill imgFill">
      <img src="/styles/images/news/hero.jpg" alt="" /><!-- 1920 * 600 px -->
    </div><!-- // page-hero-bg -->
    <div class="page-hero-inner container">
      <div class="page-hero-content text-white" data-aos="fade-down">
        <h1 class="title fw-700 lh-125 mb-0">推動自行車世界的進化</h1>
      </div>
    </div><!-- // page-hero-inner -->
  </div><!-- // page-hero -->
  <div class="page-nav">
    <div class="page-nav-inner container">
      <div class="page-nav-swiper swiper-container">
        <div class="swiper-wrapper">
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/news" data-sub-category="news">最新消息</a></div>
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/news02" data-sub-category="news02">新聞集錦</a></div>
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/news03" data-sub-category="news03">新聞聯絡人</a></div>
        </div>
      </div><!-- // page-nav-swiper -->
    </div><!-- // page-nav-inner -->
  </div><!-- // page-nav -->
</div><!-- // page-top -->
```

#### D. 創新科技（Banner非滿版，導覽列在上方）

！！！我突然發現`styles/sass/layouts/pages/_brands.sass`有一段`.brands-top`被我註解掉，應該是我在測試的時候忘了改回來，結果跑版也沒人發現.....XD  
（參考：[http://html.m000322.24241872.tw/technology01](http://html.m000322.24241872.tw/technology01)）
```html
<div class="page-top brands-top default has-nav">
  <div class="page-nav">
    <div class="page-nav-inner container">
      <div class="page-nav-swiper swiper-container">
        <div class="swiper-wrapper">
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/technology" data-sub-category="technology">創新概況</a></div>
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/technology01" data-sub-category="technology01">智能製造</a></div>
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/technology02" data-sub-category="technology02">材料技術</a></div>
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/technology03" data-sub-category="technology03">自行車生態圈</a></div>
          <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/footprint">全球製造網路</a></div>
        </div>
      </div><!-- // page-nav-swiper -->
    </div><!-- // page-nav-inner -->
  </div><!-- // page-nav -->
  <div class="tech-hero">
    <div class="tech-hero-bg imgFill" data-aos="fade">
      <img src="/styles/images/technology/01/hero.jpg" alt="" /><!-- 1920 * 770 px -->
    </div><!-- // tech-hero-bg -->
    <div class="tech-hero-inner container">
      <div class="tech-hero-content aos-small" data-aos="fade-up">
      ......
      </div>
    </div><!-- // tech-hero-inner -->
  </div><!-- // tech-hero -->
</div><!-- // page-top -->
```

### 【當前頁面】
自動標記當前頁面的功能，目前做到三層分類  
這邊名稱有點複雜，因為當時改來改去QQ...不過概念都是相同的
#### 第一層分類（header）
各個大分類（關於我們，品牌與服務，創新科技...）都有標記`data-category`，沒有的可以再補上去
```html
<!-- header.php -->
<nav class="mainlinks">
  <ul class="list-unstyled">
    <li class="ml-category" data-category="about">...</li>
    <li class="ml-category" data-category="brands">...</li>
    ...
  </ul>
</nav>
```
在頁面的`<div class="wp">`加上`data-category`就可以標記該分類  
```html
<!-- vision.php -->
<div class="wp" data-category="about">
  ...
</div>

<!-- header.php -->
<nav class="mainlinks">
  <ul class="list-unstyled">
    <li class="ml-category current" data-category="about">...</li> <!-- 自動加上current -->
    ...
  </ul>
</nav>
```
#### 第二層分類（page-nav）
相同的概念，在第二層分類加上`data-sub-category`
```html
<!-- _about-page-top.php -->
<div class="page-nav">
  <div class="page-nav-inner container">
    <div class="page-nav-swiper swiper-container">
      <div class="swiper-wrapper">
        <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/vision" data-sub-category="info">集團簡介</a></div>
        <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/group" data-sub-category="management">集團經營與管理</a></div>
        <div class="page-nav-item swiper-slide"><a class="page-nav-item-link" href="/footprint" data-sub-category="footprint">全球版圖</a></div>
      </div>
    </div><!-- // page-nav-swiper -->
  </div><!-- // page-nav-inner -->
</div><!-- // page-nav -->
```
一樣在頁面的`<div class="wp">`加上`data-sub-category`就可以標記該分類  
```html
<!-- vision.php -->
<div class="wp" data-category="about" data-sub-category="info">
  ...
</div>
```
#### 第三層分類（page-subnav）
第三層分類使用`data-page`  
（註：`<div class="page-subnav-toggle">`手機版才會出現，文字顯示目前分類）
```html
<!-- _about-page-subnav.php -->
<div class="page-subnav">
  <div class="page-subnav-toggle">
    <span class="page-subnav-toggle-txt"></span>
  </div><!-- // page-subnav-toggle -->
  <div class="page-subnav-menu">
    <ul class="list-unstyled d-sm-flex justify-content-sm-center align-items-sm-center">
      <li class="page-subnav-item"><a class="page-subnav-item-link" href="/vision" data-page="vision">目標與承諾</a></li>
      <li class="page-subnav-item"><a class="page-subnav-item-link" href="/policy" data-page="policy">集團策略</a></li>
      <li class="page-subnav-item"><a class="page-subnav-item-link" href="/history" data-page="history">巨大沿革</a></li>
      <li class="page-subnav-item"><a class="page-subnav-item-link" href="/contact" data-page="contact">聯絡我們</a></li>
    </ul>
  </div><!-- // page-subnav-menu -->
</div><!-- // page-subnav -->
```
同理，在頁面的`<div class="wp">`加上`data-page`就可以標記該分類  
```html
<!-- vision.php -->
<div class="wp" data-category="about" data-sub-category="info" data-page="vision">
  ...
</div>
```
