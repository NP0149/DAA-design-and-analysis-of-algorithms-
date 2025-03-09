# Merge Sort 

designed to sort the array for large amount of data

# Approch

recurrsively divide the array by finding the mid value and then sort the individual divided arrays and then merge them together

```C
 #include<stdio.h>
void merge(int arr[],int st,int mid,int end){
 int i=0,j=0,k=st;
 int n1=mid-st+1;
 int n2=end-mid;
 int left[n1];
 int right[n2];
 for(int i=0;i<n1;i++){
 left[i]=arr[st+i];
 }
 for(int j=0;j<n2;j++){
right[j]=arr[mid+1+j];
}
 while(i<n1 && j<n2){
 if(left[i]<=right[j])
 arr[k++]=left[i++];
 else
 arr[k++]=right[j++];
 }
 while(i<n1){
 arr[k++]=left[i++];
 }
 while(j<n2){
arr[k++]=right[j++];
}
}
void mergesort(int arr[],int st,int end){
if(st>=end)
return;
 int mid=st+(end-st)/2;
 mergesort(arr,st,mid);
 mergesort(arr,mid+1,end);
 merge(arr,st,mid,end);
 }
int main(){
int arr[]={3,2,1};
int n=sizeof(arr)/sizeof(arr[0]);
mergesort(arr,0,n-1);
for(int i=0;i<n;i++){
 printf("%d ",arr[i]);
 }
 return 0;
 }
 ```

# complexities

Time complexity:

best,avg,worst time complexities: O(nlogn)

space complexity:O(n)//to store the divided arrays need extra space
