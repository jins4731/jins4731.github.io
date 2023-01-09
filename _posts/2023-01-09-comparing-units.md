---
title: CSS-px, %, em, rem 정리
author: jins4731
date: 2023-01-09 22:30:00 +0900
categories: [Frontend, CSS]
tags: [CSS]
pin: true
---

# Comparing Units (specifically for font-size)

## px

- Easy to understand & translateable
- Limited user focus & not scalable

## %

- Relative to parent element Size
- Hard to manage due to cascading nature
  > 부모 요소 참조
  > style 속성에 따라 참조하는 요소가 달라질 수 있다.

## em

- Relative to parent element Size
- Size is relative to font-size
- Hard to manage due to cascading nature
  > 부모 요소의 font-size 참조
  > 부모 요소의 font-size 를 정해놓지 않으면 font-size의 값은 브라우저의 기본 font-size 값으로 설정된다.
  > 1em == 100%
  > 2em == 200%

## rem

- Size is relative to root element's font size
- Preferred choice if applicable
  > 최상위 요소의 font-size 참조
  > 최상위 요소의 font-size가 설정되어 있으면 hmtl 요소의 값을 기준으로 font-size 가 결정된다.
  > 최상위 요소 html의 font-size가 설정되어 있지 않으면 font-size 의 값은 브라우저의 기본 font-size 를 기준으로 설정된다.

## % 와 em 의 차이

- %  
  style 속성에 따라, 부모 요소의 다른 요소를 참조한다.
  예를 들어, font-size 속성에서는 부모 요소의 font-size 를 참조하지만, padding 에서는 부모 요소의 width 값을 참조한다.
- em  
  모든 style 속성에서 부모 요소의 font-size 속성을 참조한다.
  예를 들어, padding 속성 에서 부모 요소의 font-size 의 값을 참조한다.
  > 이 규칙은 rem 에도 적용이 된다.
