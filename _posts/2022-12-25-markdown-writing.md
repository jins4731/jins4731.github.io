---
title: 마크다운 작성법 자주쓰는 명령어 정리
author: jins4731
date: 2022-12-25 16:20:00 +0900
categories: [Language, MarkDown]
tags: [MarkDown]
pin: true
---

# MarkDown 작성법

## MarkDown 이란?

- 2004년 존그루버의 의해 만들어짐
- 쉽게 쓰고 읽을 수 있으며, HTML로 변환 가능
- 개발자들이 버전관리/협업도구 텍스트 문서로 선호
- [GitHub](https://github.com) Repository 정보를 기록하는 README.md 를 통해 각광받음

## MarkDown 장단점

### 장점

```
1. 간결하고 읽고 쓰기 쉽다.
2. 키보드로 쉽게 조작하여 구조적인 글쓰기가 가능하다.
3. 다양한 형태로 변환이 가능하다
4. 텍스트(Text)로 저장되기 때문에 용량이 적어 보관이 용이하다
5. 텍스트 파일이기 때문에 변경이력 관리를 쉽게 할 수 있다.
6. 지원하는 프로그램과 플랫폼이 다양하다
```

### 단점

```
1. 표준이 없다.
2. 표준이 없기 때문에 도구에 따라서 변환방식이나 생성물이 다르다.
3. 모든 HTML 마크업을 대신하지 못한다.
4. 뷰어의 속도가 느리다
```

## MarkDown 문법

> MarkDown Guide 참조 : [MarkDown Guide](https://www.markdownguide.org/basic-syntax/#overview)

### \- 헤더 (Header)

#### 문법

```
# This is a H1
## This is a H2
### This is a H3
#### This is a H3
##### This is a H4
###### This is a H5
```

#### 표시

# This is a H1

## This is a H2

### This is a H3

#### This is a H3

##### This is a H4

###### This is a H5

---

### \- 블럭인용문자 (BlockQuote)

#### 문법

```
> This is a first blockquote.
>    > This is a first blockquote.
>    >    > This is a first blockquote.
```

#### 표시

> This is a first blockquote.
>
> > This is a first blockquote.
> >
> > > This is a first blockquote.

---

### \- 목록 (List)

#### 1\. 순서있는 목록

#### 문법

```
1. 첫번째
2. 두번째
3. 세번째
```

#### 표시

1.  첫번째
2.  두번째
3.  세번째

---

#### 2\. 순서없는 목록

#### 문법

```
* 빨강
    * 녹색
        * 파랑

+ 빨강
    + 녹색
        + 파랑

- 빨강
    - 녹색
        - 파랑
```

#### 표시

- 빨강
  - 녹색
    - 파랑
- 빨강
  - 녹색
    - 파랑
- 빨강
  - 녹색
    - 파랑

---

### \- 코드 (code)

#### 문법

```
this is a normal paragraph:
    this is a code block.
    four space or tab
end code block
```

#### 표시

this is a normal paragraph:

```
this is a code block.
four space or tab
```

end code block

---

### \- 코드블럭 (CodeBlock)

#### 1\. pre, code 이용방식

#### 문법

```
<pre>
<code>
public class Test{
    public static void main(String[] args){
        System.out.println("Hello, World");
    }
}
</code>
</pre>
```

#### 표시

```
public class Test{
 public static void main(String[] args){
  System.out.println("Hello, World");
 }
}
```

#### 2\. 코드블록코드(''\`\`\`'') 이용방식

#### 문법

````
```
public class Test{
    public static void main(String[] args){
        System.out.println("Hello, World");
    }
}
```
````

#### 표시

```
public class Test{
     public static void main(String[] args){
          System.out.println("Hello, World");
     }
}
```

> [문법 강조(Syntax highlightin)](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/creating-and-highlighting-code-blocks#syntax-highlighting)
>
> ````
> ```java
> public class Test{
>     public static void main(String[] args){
>         System.out.println("Hello, World");
>     }
> }
> ㅤ```
> ````
>
> ```
> public class Test{
>     public static void main(String[] args{
>         System.out.println("Hello, World");
>    }
> }
> ```

---

### \- 수평선 (Horizontal Rules)

#### 문법

```
 ***
 ---
 ____________
```

#### 표시

---

---

---

---

### \- 링크 (Link)

#### 문법

```
Link: [Google](https://google.com "Go google")
```

#### 표시

Link: [Google](https://google.com "Go google")

### \- 강조 (Emphasis)

#### 문법

```
*single asterisks*
_single underscores_
**double underscores__
~~cancelline~~
```

#### 표시

_single asterisks_  
_single underscores_  
\*\*double underscores\_\_

~cancelline~

---
