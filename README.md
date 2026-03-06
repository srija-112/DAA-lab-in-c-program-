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
