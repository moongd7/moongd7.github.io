---
layout: post
title:  "합병정렬"
date:   2023-03-19 15:33:00 +0900
categories: none
---
합병정렬

    public class MergeSort {

    // 분할(Divide) 단계
    public static void mergeSort(int[] arr, int left, int right) {
        // left 인덱스가 right 인덱스보다 작을 때까지 반복
        if (left < right) {
            int mid = (left + right) / 2; // 배열을 중간 지점(mid)으로 나눔
            mergeSort(arr, left, mid); // 왼쪽 부분 배열을 재귀적으로 분할
            mergeSort(arr, mid + 1, right); // 오른쪽 부분 배열을 재귀적으로 분할
            merge(arr, left, mid, right); // 분할된 부분 배열을 합병
        }
    }

    // 합병(Merge) 단계
    public static void merge(int[] arr, int left, int mid, int right) {
        int[] temp = new int[right - left + 1]; // 합병 결과를 저장할 임시 배열 생성
        int i = left; // 왼쪽 부분 배열의 시작 인덱스
        int j = mid + 1; // 오른쪽 부분 배열의 시작 인덱스
        int k = 0; // 임시 배열의 인덱스

        // 왼쪽과 오른쪽 부분 배열의 원소를 비교하여 작은 값을 임시 배열에 저장
        while (i <= mid && j <= right) {
            if (arr[i] <= arr[j]) {
                temp[k++] = arr[i++];
            } else {
                temp[k++] = arr[j++];
            }
        }

        // 왼쪽 부분 배열에 남은 원소들을 임시 배열에 저장
        while (i <= mid) {
            temp[k++] = arr[i++];
        }

        // 오른쪽 부분 배열에 남은 원소들을 임시 배열에 저장
        while (j <= right) {
            temp[k++] = arr[j++];
        }

        // 임시 배열에 저장된 원소들을 원래 배열에 복사
        for (int x = 0; x < temp.length; x++) {
            arr[left + x] = temp[x];
        }
    }

    public static void main(String[] args) {
        int[] arr = {5, 1, 9, 3, 7, 6, 8, 2, 4}; // 정렬할 배열
        mergeSort(arr, 0, arr.length - 1); // 합병정렬 실행
        System.out.println(Arrays.toString(arr)); // 정렬된 배열 출력
    }
}


