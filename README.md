# CPP-program-to-sort-elements-of-the-given-array

Sort Elements of the Given Array in C++
Here, in this page we will discuss the program to sort elements of the given array in C++ programming language. We will discuss various algorithms to sort the given input array.

Method Discussed :
Method 1 : Using Naive Approach.
Method 2 :Using inbuilt sort() function.
Method 3 : Using heap sort.
Let’s discuss above methods one by one,

Method 1 :
Run a loop from 0 to n-1
Inside that loop run another loop from i+1 to n
Check if(arr[i]>arr[j])
Swap arr[i] with arr[j]
Method 1 : Code in C++
Run
#include<bits/stdc++.h>
using namespace std;

void sorted(int arr[], int n){

  for(int i=0; i<n-1; i++){
     for(int j=i+1; j<n; j++){ if(arr[i]>arr[j]){
             int temp = arr[i];
             arr[i] = arr[j];
             arr[j] = temp;
          }
     }
   }

   for(int i=0; i<n; i++)
      cout<<arr[i]<<" ";
}

int main(){

   int arr[] = {10, 89, 67, 45, 83, 9, 12};
   int n = sizeof(arr)/sizeof(arr[0]);

   sorted(arr, n);
}
Output
9 10 12 45 67 83 89
Method 2 :
Call inbuilt sort() function to sort the array
Pass arr, arr+n to the sort function.
About sort() function
Sort is an in-built function in a C++ STL ( Standard Template Library).
This function is used to sort the elements in the range in ascending or descending order.
Time Complexity : O(nlogn)
Method 2 : Code in C++
Run
#include<bits/stdc++.h>
using namespace std;

void sorted(int arr[], int n){

   sort(arr, arr+n);

   for(int i=0; i<n; i++)
      cout<<arr[i]<<" ";
}

int main(){

   int arr[] = {10, 89, 67, 45, 83, 9, 12};
   int n = sizeof(arr)/sizeof(arr[0]);

   sorted(arr, n);
}
Output
9 10 12 45 67 83 89
Related Pages
Reverse an Array

Sort first half in ascending order and second half in descending

Finding the frequency of elements in an array

Sorting elements of an array by frequency

Finding the Longest Palindrome in an Array

Method 3 :
To sort any array into a logical order(using heap sort) following steps are followed :-

Convert the array into heap.
Now convert this heap into max heap.
As the heap is converted to max heap largest element in the list is stored in the root of the heap, replace it with the last item of the heap.
Now delete this node and reduce the size of heap by 1.
Follow these steps until the list is sorted.
C++ program to sort the given array
Method 3 : Code in C++
Run
#include<bits/stdc++.h>
using namespace std;

// To heapify a subtree rooted with node i which is
// an index in arr[]. n is size of heap
void heapify(int arr[], int n, int i)
{
    int largest = i; // Initialize largest as root
    int l = 2 * i + 1; // left = 2*i + 1
    int r = 2 * i + 2; // right = 2*i + 2

    // If left child is larger than root
    if (l < n && arr[l] > arr[largest])
      largest = l;

    // If right child is larger than largest so far
    if (r < n && arr[r] > arr[largest])
       largest = r;

   // If largest is not root
   if (largest != i) {
     swap(arr[i], arr[largest]);

   // Recursively heapify the affected sub-tree
   heapify(arr, n, largest);
  }
}

// main function to do heap sort
void heapSort(int arr[], int n)
{
     // Build heap (rearrange array)
    for (int i = n / 2 - 1; i >= 0; i--)
      heapify(arr, n, i);

     // One by one extract an element from heap
     for (int i = n - 1; i > 0; i--) {
    
     // Move current root to end
     swap(arr[0], arr[i]);

     // call max heapify on the reduced heap
     heapify(arr, i, 0);
   }

   for(int i=0; i<n; i++)
      cout<<arr[i]<<" ";
}

int main(){

   int arr[] = {10, 89, 67, 45, 83, 9, 12};
   int n = sizeof(arr)/sizeof(arr[0]);

   heapSort(arr, n);
}
Output
9 10 12 45 67 83 89
