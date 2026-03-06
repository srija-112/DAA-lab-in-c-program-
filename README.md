# DAA-lab-in-c-program-#include <stdio.h>
//linear search 
#include <stdio.h>
int main() {
    int arr[] = {4, 7, 1, 9, 3};
    int n = 5;
    int key = 9;
    int i, pos = -1;
    for(i = 0; i < n; i++) {
        if(arr[i] == key) {
            pos = i;
            break;
        }
    }
    if(pos != -1)
        printf("Element found at position %d", pos + 1);
    else
        printf("Element not found");
    return 0;
}

//Binary search 
#include <stdio.h>
int main() {
    int arr[100], n, key;
    int low = 0, high, mid, i, pos = -1;
    printf("Enter number of elements: ");
    scanf("%d", &n);

    printf("Enter sorted elements:\n");
    for(i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("Enter element to search: ");
    scanf("%d", &key);
    high = n - 1;
    while(low <= high) {
        mid = (low + high) / 2;
        if(arr[mid] == key) {
            pos = mid;
            break;
        }
        else if(arr[mid] < key)
            low = mid + 1;
        else
            high = mid - 1;
    }
    if(pos != -1)
        printf("Element found at position %d", pos + 1);
    else
        printf("Element not found");
    return 0;
}

//bubble sort 
int main() {
    int arr[] = {9, 3, 7, 1, 5};
    int n = 5;
    int i, j, temp;
    for(i = 0; i < n - 1; i++) {
        for(j = 0; j < n - i - 1; j++) {
            if(arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }

    printf("Sorted array:\n");
    for(i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}

//modified Bubble sort 
#include <stdio.h>
int main() {
    int arr[100], n, i, j, temp, flag;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    printf("Enter elements:\n");
    for(i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }
    for(i = 0; i < n - 1; i++) {
        flag = 0;
        for(j = 0; j < n - i - 1; j++) {
            if(arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
                flag = 1;
            }
        }
        if(flag == 0)
            break;
    }
    printf("Sorted array:\n");
    for(i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    return 0;
}
//write a c program whose time complexity is exactly T(n)=3n^2+2n+4

#include <stdio.h>
int main() {
    int n, i, j, k = 0;
    printf("Enter n: ");
    scanf("%d", &n);
    for(i = 0; i < n; i++)
        for(j = 0; j < n; j++)
            k++;
    for(i = 0; i < n; i++)
        for(j = 0; j < n; j++)
            k++;
    for(i = 0; i < n; i++)
        for(j = 0; j < n; j++)
            k++;
    for(i = 0; i < 2 * n; i++)
        k++;
    k++;
    k++;
    k++;
    k++;
    printf("Total operations: %d\n", k);

    return 0;
}

//constract a c program whose execution time follows T(n)=n^3+nlogn+20.
#include <stdio.h>
int main() {
    int n, i, j, k, m = 0;
    printf("Enter n: ");
    scanf("%d", &n); 
    for(i = 0; i < n; i++)
        for(j = 0; j < n; j++)
            for(k = 0; k < n; k++)
                m++;
    for(i = 1; i <= n; i++)
        for(j = 1; j <= n; j = j * 2)
            m++;   
    for(i = 0; i < 20; i++)
        m++;

    printf("Total operations: %d\n", m);
    return 0;
}

design a c program that runs in T(n)=nlogn+5n+10.
#include <stdio.h>

int main() {
    int n, i, j, count = 0;
    printf("Enter n: ");
    scanf("%d", &n);   
    for(i = 1; i <= n; i++)
        for(j = 1; j <= n; j = j * 2)
            count++; 
    for(i = 0; i < 5 * n; i++)
        count++;  
    for(i = 0; i < 10; i++)
        count++;

    printf("Total operations = %d\n", count);
    return 0;
}

write a c program that exhibits  an exponential time complexity of T(n)=n(n+1)/2.
#include <stdio.h>
int main() {
    int n, i, j;
    int count = 0;
    printf("Enter value of n: ");
    scanf("%d", &n);
    for(i = 1; i <= n; i++) {
        for(j = 1; j <= i; j++) {
            printf("* ");
            count++;
        }
        printf("\n");
    }
    printf("Total operations = %d\n", count);
    return 0;
}

write down a sorting algorithm which recurrence relation is T(n)=2T(n/2)+n.

#include <stdio.h>
void merge(int arr[], int left, int mid, int right) {
    int i, j, k;
    int n1 = mid - left + 1;
    int n2 = right - mid;
    int L[n1], R[n2];
    for(i = 0; i < n1; i++)
        L[i] = arr[left + i];
    for(j = 0; j < n2; j++)
        R[j] = arr[mid + 1 + j];
    i = 0; j = 0; k = left;
    while(i < n1 && j < n2) {
        if(L[i] <= R[j]) {
            arr[k] = L[i++];
        } else {
            arr[k] = R[j++];
        }
        k++;
    }
    while(i < n1) arr[k++] = L[i++];
    while(j < n2) arr[k++] = R[j++];
    printf("After merging from index %d to %d: ", left, right);
    for(int x = left; x <= right; x++)
        printf("%d ", arr[x]);
    printf("\n");
}
void mergeSort(int arr[], int left, int right) {
    if(left < right) {
        int mid = (left + right) / 2;
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}
int main() {
    int arr[] = {38, 27, 43, 3, 9, 82, 10};
    int n = sizeof(arr)/sizeof(arr[0]);
    printf("Original array: ");
    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n\n");
    mergeSort(arr, 0, n - 1);
    printf("\nSorted array: ");
    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n");
    return 0;
}
write down a sorting algorithm which recurrence relation is T(n)=T(n-1)+n.

#include <stdio.h>
int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    for(int j = low; j < high; j++) {
        if(arr[j] <= pivot) {
            i++;
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }
    int temp = arr[i+1];
    arr[i+1] = arr[high];
    arr[high] = temp;
    return i+1;
}
void quickSortRecursive(int arr[], int low, int high) {
    if(low < high) {
        int pi = partition(arr, low, high);
        printf("After partition with pivot %d: ", arr[pi]);
        for(int k = low; k <= high; k++)
            printf("%d ", arr[k]);
        printf("\n");
        quickSortRecursive(arr, low, pi-1);
        quickSortRecursive(arr, pi+1, high);
    }
}

int main() {
    int arr[] = {5, 4, 3, 2, 1};
    int n = sizeof(arr)/sizeof(arr[0]);

    printf("Original array: ");
    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n\n");
    quickSortRecursive(arr, 0, n-1);
    printf("\nSorted array: ");
    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n");
    return 0;
}

write down a searching algorithm forT(n)=T(n/2)+c.

#include <stdio.h>
void binarySearchTrace(int arr[], int n, int key) {
    int left = 0, right = n - 1;
    int pass = 1;
    printf("Original array: ");
    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n\n");
    while(left <= right) {
        int mid = left + (right - left) / 2;
        printf("Pass %d: search range [%d...%d], mid=%d, value=%d\n",
               pass, left, right, mid, arr[mid]);
        pass++;
        if(arr[mid] == key) {
            printf("\nElement %d found at index %d\n", key, mid);
            return;
        } else if(arr[mid] > key) {
            right = mid - 1;
        } else {
            left = mid + 1;
        }
    }
    printf("\nElement %d not found\n", key);
}
int main() {
    int arr[] = {1, 3, 5, 7, 9, 11, 13};
    int n = sizeof(arr) / sizeof(arr[0]);
    int key = 7;

    binarySearchTrace(arr, n, key);
    return 0;
}
//selection sort 

#include <stdio.h>
int findMinIndex(int arr[], int start, int n) {
    int minIndex = start;
    for(int i = start+1; i < n; i++) {
        if(arr[i] < arr[minIndex])
            minIndex = i;
    }
    return minIndex;
void selectionSortRecursive(int arr[], int start, int n, int pass) {
    if(start >= n-1)
        return;
    int minIndex = findMinIndex(arr, start, n);
    if(minIndex != start) {
        int temp = arr[start];
        arr[start] = arr[minIndex];
        arr[minIndex] = temp;
    }
    printf("Pass %d: ", pass);
    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n");
    selectionSortRecursive(arr, start + 1, n, pass + 1);
}
int main() {
    int arr[] = {64, 25, 12, 22, 11};
    int n = sizeof(arr)/sizeof(arr[0]);

    printf("Original array: ");
    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n\n");
    selectionSortRecursive(arr, 0, n, 1);
    printf("\nSorted array: ");
    for(int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n");

    return 0;
}

//Insertion sort 
#include <stdio.h>
void insertRecursive(int arr[], int n) {
    if (n <= 1)
        return;
    insertRecursive(arr, n - 1);
    int last = arr[n - 1];
    int j = n - 2;
    while (j >= 0 && arr[j] > last) {
        arr[j + 1] = arr[j];
        j--;
    }
    arr[j + 1] = last;
    printf("Pass %d: ", n - 1);
    for (int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n");
}
int main() {
    int arr[] = {12, 11, 13, 5, 6};
    int n = sizeof(arr) / sizeof(arr[0]);
    printf("Original array: ");
    for (int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n\n");
    insertRecursive(arr, n);
    printf("\nSorted array: ");
    for (int i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n");
    return 0;
}

//matrix multiplication 

#include <stdio.h>
int multiplyElement(int A[][3], int B[][3], int row, int col, int k, int n) {
    if (k < 0)
        return 0;
    return multiplyElement(A, B, row, col, k-1, n) + A[row][k] * B[k][col];
}
void multiplyMatrixRecursive(int A[][3], int B[][3], int C[][3], int row, int col, int n) {
    if (row >= n)
        return;
    if (col >= n) {
        multiplyMatrixRecursive(A, B, C, row + 1, 0, n);
        return;
    }

    C[row][col] = multiplyElement(A, B, row, col, n-1, n);
    printf("Computed C[%d][%d] = %d\n", row, col, C[row][col]);

    multiplyMatrixRecursive(A, B, C, row, col + 1, n);
}
int main() {
    int n = 3;
    int A[3][3] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };
    int B[3][3] = {
        {9, 8, 7},
        {6, 5, 4},
        {3, 2, 1}
    };
    int C[3][3] = {0};
    printf("Matrix A:\n");
    for(int i = 0; i < n; i++){
        for(int j = 0; j < n; j++)
            printf("%d ", A[i][j]);
        printf("\n");
    }
    printf("\nMatrix B:\n");
    for(int i = 0; i < n; i++){
        for(int j = 0; j < n; j++)
            printf("%d ", B[i][j]);
        printf("\n");
    }
    printf("\nMatrix multiplication passes:\n");
    multiplyMatrixRecursive(A, B, C, 0, 0, n);
    printf("\nResultant Matrix C = A * B:\n");
    for(int i = 0; i < n; i++){
        for(int j = 0; j < n; j++)
            printf("%d ", C[i][j]);
        printf("\n");
    }
    return 0;
}

//counting sort.

#include <stdio.h>
#include <stdlib.h>
int main() {
    int n, i, max = 0;
    scanf("%d", &n); 
    int arr[n];
    for(i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
        if(arr[i] > max)
            max = arr[i]; // Find max element
    }
    int count[max + 1];
    for(i = 0; i <= max; i++)
        count[i] = 0;
    for(i = 0; i < n; i++)
        count[arr[i]]++;
    for(i = 1; i <= max; i++)
        count[i] += count[i - 1];
    int output[n];
    for(i = n - 1; i >= 0; i--) {
        output[count[arr[i]] - 1] = arr[i];
        count[arr[i]]--;
    }
    for(i = 0; i < n; i++)
        arr[i] = output[i];
    for(i = 0; i < n; i++)
        printf("%d ", arr[i]);
    printf("\n");
    return 0;
}

