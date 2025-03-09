# Binary Search

divide the array to mid and then find the element in that particular half array,it is the optimal way for searching

```C
#include<stdio.h>
int binarysearch(int arr[],int st,int end,int key){
int mid=st+(end-st)/2;
  if(arr[mid]==key)
  return mid+1;
  else if(arr[mid]>key){
   return binarysearch(arr,st,mid-1,key);
   }
   else{
 return binarysearch(arr,mid+1,end,key);
 }
 return -1;
 }
int main(){
 int arr[]={1,2,3,4,5,6};
 int n=sizeof(arr)/sizeof(arr[0]);
 int key;
 printf("enter the key ele");
 scanf("%d",&key);
 int pos=binarysearch(arr,0,n-1,key);
 if(pos==-1){
 printf("element is not found");
 }
 else
 printf("key found at %d ",pos);
 }
```

# complexities

time:O(logn);
space:O(logn);//recurrsion

  O(1);//iterative method
