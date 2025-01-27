---
layout: single
title: "MarkDown 작성 시 참고할 수 있는 문법"
categories: coding
tag: [coding, markdown]
toc: true
toc_sticky: true
toc_label: 목차
toc_icon: "fas fa-table-tennis"
author_profile: true
sidebar: 
    nav: "docs"
search: true # 이러면 search 안됨
use_math: true
sidebar:
    nav: "counts"
# redirect_from:
#     - /coding/first3 # 또다른 url을 추가하는 방법
---


**[공지사항 넣기]**{: .notice--danger}
## 1. URL 연동하는 방법
```xml
[여기를 클릭하면 홈페이지로 이동합니다.](https://corecodet.github.io/)
```
[여기를 클릭하면 홈페이지로 이동합니다.](https://corecodet.github.io/)

<!-- ## 1. 여러가지 기능들 
1번{: .notice--primary} -->

## 2. 글씨 색 및 형광펜 칠하기
### 2.1 글씨 색 수정
```xml
<span style="color:red"> red </span>    
<span style="color:yellow"> yellow </span>   
<span style="color:blue"> blue </span>   
<span style="color:brown"> brown </span>   
<span style="color:orange"> orange </span>   
<span style="color:green"> green </span>   
<span style="color:violet"> violet </span>   
<span style="color:yellowgreen"> yellowgreen </span>    
<span style="color:blueviolet"> blueviolet </span>    
<span style="color:gray"> gray </span>   
<span style="color:indigo"> indigo </span>
```
<span style="color:red"> red  </span>    
<span style="color:yellow"> yellow </span>   
<span style="color:blue"> blue </span>   
<span style="color:brown"> brown </span>   
<span style="color:orange"> orange </span>   
<span style="color:green"> green </span>   
<span style="color:violet"> violet </span>   
<span style="color:yellowgreen"> yellowgreen </span>    
<span style="color:blueviolet"> blueviolet </span>    
<span style="color:gray"> gray </span>   
<span style="color:indigo"> indigo </span>

### 2.2 형광펜 칠하기
```xml
<mark style='background-color: #f6f8fa'> 연한 회색 </mark>    
<mark style='background-color: #f1f8ff'> 연한 파랑 </mark>    
<mark style='background-color: #fff5b1'> 연한 노랑 </mark>    
<mark style='background-color: #ffdce0'> 연한 빨강 </mark>    
<mark style='background-color: #dcffe4'> 연한 초록 </mark>    
<mark style='background-color: #f5f0ff'> 연한 보라 </mark>    
```                                                       
<mark style='background-color: #f6f8fa'> 연한 회색 </mark>    
<mark style='background-color: #f1f8ff'> 연한 파랑 </mark>    
<mark style='background-color: #fff5b1'> 연한 노랑 </mark>    
<mark style='background-color: #ffdce0'> 연한 빨강 </mark>    
<mark style='background-color: #dcffe4'> 연한 초록 </mark>    
<mark style='background-color: #f5f0ff'> 연한 보라 </mark>    

## 4. box 작성
```xml
<div class="notice--success">
<h4>Box</h4>
<ul>
    <li> 순서 1 </li>
    <li> 순서 2 </li>
    <li> 순서 3 </li>
</ul>
</div>
```
<div class="notice--success">
<h4>Box</h4>
<ul>
    <li> 순서 1 </li>
    <li> 순서 2 </li>
    <li> 순서 3 </li>
</ul>
</div>

## 4. 버튼 작성
```md
[google 사이트로 연결](https://google.com){: .btn .btn--danger}
```
[google 사이트로 연결](https://google.com){: .btn .btn--danger}


## 5. 화면의 width 조절 방법
foler: ../_sass/_minimal-mistakes/_variables.scss
```scss
$right-sidebar-width-narrow: 100px !default;    // default 200px
$right-sidebar-width: 200px !default;           // default 300px
$right-sidebar-width-wide: 250px !default;      // default 400px
```

## 6. Font 
### 6.1 Font 변경하는 방법 
font를 변경하기 위해서는 두 파일을 수정해야 함
1. folder: ../assets/css/main.scss 에 아래 코드 추가
```scss
@font-face {
    font-family: 'MaplestoryOTFLight';
    src: url('https://cdn.jsdelivr.net/gh/fontbee/font@main/Nexon/MaplestoryOTFLight.woff') format('woff');
    font-weight: 300;
    font-style: normal;
}
```
2. foler: ../_sass/_minimal-mistakes/_variables.scss
```scss
$sans-serif: -apple-system, BlinkMacSystemFont,"MaplestoryOTFLight", "Roboto", "Segoe UI",
  "Helvetica Neue", "Lucida Grande", Arial, sans-serif !default;
```
### 6.2 Font 크기 조절하는 방법
folder: ../_sass/_minimal-mistakes/_reset.scss
```scss
html {
  /* apply a natural box layout model to all elements */
  box-sizing: border-box;    
  background-color: $background-color;
  font-size: 16px;                
  @include breakpoint($medium) {
    font-size: 16px;              
  }
  @include breakpoint($large) {
    font-size: 16px;              
  }
  @include breakpoint($x-large) {
    font-size: 16px;              
  }
  -webkit-text-size-adjust: 100%;
  -ms-text-size-adjust: 100%;
}
```


## 7. 밑줄 제거 방법
폴더: ../_sass/_minimal-mistakes/_base.scss
```scss
a {
  text-decoration: none; // Add this code

  &:focus {
    @extend %tab-focus;
  }
  &:visited {
    color: $link-color-visited;
  }
  &:hover {
    color: $link-color-hover;
    outline: 0;
  }
}
```