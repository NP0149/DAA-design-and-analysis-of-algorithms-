# Fractional Knapsack

```
#include<stdio.h>
#include<stdlib.h>
typedef struct{
 int value,weight;
 }item;
 int compare(const void *a,const void *b){
  double r1=((item*)a)->value/(double)((item*)a)->weight;
  double r2=((item*)b)->value/(double)((item*)b)->weight;
  return (r2>r1)-(r2<r1);
  }
 double fracknap(int capacity,item list[],int n){
 qsort(list,n,sizeof(item),compare);
 double totalvalue=0.0;
 for(int i=0;i<n;i++){
 if(capacity>=list[i].weight){
 capacity-=list[i].weight;
 totalvalue+=list[i].value;
 }
 else{
 totalvalue+=list[i].value*((double)capacity/list[i].weight);
 break;
 }
 }
 return totalvalue;
 }
 int main(){
 item list[]={{60,10},{100,20},{120,30}};
 int capacity=50;
 int n=sizeof(list)/sizeof(list[0]);
 double maxvalue=fracknap(capacity,list,n);
 printf("the max value is %lf",maxvalue);
 return 0;
 }

```

# Time complexity

n=no.of items
t(n)=O(nlogn)
