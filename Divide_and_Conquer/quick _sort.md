# Quick Sort

to sort the elements in the array for large amount of data

# Approach

consider the starting element as pivot arrange all the elements which are less than the pivot should br present left of pivot
and the elements greater than pivot should be right side ,after every pass the pivot comes to its position.the best thing about the 
quick sort is if the array is sorted no more division takes place...

```C
#include<stdio.h>
void swap(int *a,int *b){
int temp=*a;
*a=*b;
*b=temp;
}
void quick(int arr[],int st,int end){
int pivot=arr[st];
int i=st,j=end;
if(i>j)
return;
while(i<j){
 while(arr[i]<=pivot && i<=end)
 i++;
 while(arr[j]>pivot && j>st)
 j--;
 if(i<j)
 swap(&arr[i],&arr[j]);
 }
 swap(&arr[j],&arr[st]);
 quick(arr,st,j-1);
 quick(arr,j+1,end);
 }
int main(){
int arr[]={9,8,7,6,5,4,3,2,1};
int n=sizeof(arr)/sizeof(arr[0]);
quick(arr,0,n-1);
for(int i=0;i<n;i++){
 printf("%d ",arr[i]);
 }
}
```

# complexities

Time complexity:
   best case:O(nlogn);
   avg case:O(nlogn);
   worst case:O(n^2);

space complexity:
   best case:O(logn);
   worst case:O(n);
