---
layout: post
title: 자바를 활용한 퀵 정렬
comments: true
author : 박종복
tags : [Java]
---

## 퀵정렬

# Java 코드
{% highlight java %}
import java.util.Arrays;
public class QuickSort_ver01 {

	public static void main(String[] args) {
		int[] array = {66, 10, 1, 34, 5, -10};
		sort(array, 0, array.length-1);
		for(int a : array) {
			System.out.print(" " + a);
		}
	}

	private static void sort(int[] array, int start, int end) {
		int left = start;
		int right = end;
		int pivot = array[(left+right)/2];
		
		while(left <= right) {
			System.out.println(Arrays.toString(array) + " pivot : " + pivot);
			while(array[left] < pivot) left++;   // pivot보다 큰 값을 만날때 까지 반복
			while(array[right] > pivot) right--; // pivot보다 작은 값을 만날때 까지 반복
			
			// left는 큰값을 만났고, right는 작은 값을 만났을 경우. right와 left가 크로스가 될 경우 pivot기준 partition 분류 완료.
			if(left <= right) { 
				System.out.println(array[left] + " <--> " + array[right] + " change");
				swap(array, left, right);
				System.out.println(Arrays.toString(array));
				left++; // 바꿔준 후 바꾸기 전 값을 제외하고 
				right--;// 바꿔준 후 바꾸기 전 값을 제외하고
			}
			System.out.println();
		}// while
		
		// 분할된 두개의 array를 마저 정리하자.
		if(start < right) sort(array, start, right); // 같은 방식으로 pivot보다 작은 값 정렬
		if(end > left) sort(array, left, end);	     // 같은 방식으로 pivot보다 큰 값 정렬github
	}

	private static void swap(int[] array, int left, int right) {
		int result = array[left];
		array[left] = array[right];
		array[right] = result;
	}

}

{% endhighlight %}
