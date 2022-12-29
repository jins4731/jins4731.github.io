---
title: sort-selection sort
author: jins4731
date: 2022-12-29 21:17:00 +0900
categories: [Java, Codingtest]
tags: [Java]
pin: true
---

# 정렬 알고리즘

## 선택 정렬

### 선택 정렬이란?

정렬되지 않은 데이터에서 **가장 작은 값을 뽑아 가장 앞의 데이터와 교환** 해나가는 정렬 방식

### 정렬 방법

1. 주어진 범위에서 **_최소 값의 위치_** 를 찾는다.
2. 최소 값을 해당 범위의 **_가장 앞 숫자와 자리를 바꾼다._**
3. 이후, 나머지 범위에 대해 위의 **_과정을 반복_** 한다.

### 알고리즘 구현

```java
import java.util.*;
import java.io.*;
import java.lang.*;

public class Main{
	public static final Scanner scanner = new Scanner(System.in);

	public static int getMinIndex(int[] data, int begin){
		int minIndex = begin;
		for(int i=begin; i<data.length; i++){
			if(data[minIndex]>data[i]) minIndex = i;
		}
		return minIndex;
	}

	public static int[] selectionSort(int data[]){
		for(int i=0; i<data.length-1; i++){
			int minIndex = getMinIndex(data, i);
			int temp = data[i];
			data[i] = data[minIndex];
			data[minIndex] = temp;
		}
		return data;
	}

	public static void main(String args[]){
		int n = scanner.nextInt();
		int data[] = new int[n];
		for(int i=0; i<n; i++){
			data[i] = scanner.nextInt();
		}
		data = selectionSort(data);
		for(int i=0; i<n; i++){
			System.out.printf(data[i]+" ", "%d");
		}
	}
}
```

## 삽입 정렬

### 삽입 정렬이란?

선택한 요소를 그보다 더 앞쪽의 이미 정렬된 배열 부분과 비교하여 알맞은 위치의 **삽입** 하는 작업을 반복하여 정렬

### 정렬 방법

1.  index 가 1인 요소 부터 선택하여 진행한다.
2.  n번째 index 는 **0번째 index** 부터 **n-1 번째 index** 의 요소와 비교한다.
3.  삽입할 위치를 정했다면, 해당 위치에 요소를 삽입한다.
4.  이후, 나머지 범위에 대해 위의 **_과정을 반복_** 한다.

### 알고리즘 구현

```java
import java.util.*;
import java.io.*;
import java.lang.*;

public class Main{
	public static final Scanner scanner = new Scanner(System.in);

	public static int[] insertSort(int data[]){
		for(int i=1; i<data.length; i++){
			int index = i;

			while(index > 0 && (data[index-1] > data[index])){
				int temp = data[index];
				data[index] = data[index-1];
				data[index-1] = temp;
				index--;
			}
		}
		return data;
	}

	public static void main(String args[]){
		int n = scanner.nextInt();
		int data[] = new int[n];
		for(int i=0; i<n; i++){
			data[i] = scanner.nextInt();
		}
		data = insertSort(data);
		for(int i=0; i<n; i++){
			System.out.printf(data[i]+" ", "%d");
		}
	}
}
```
