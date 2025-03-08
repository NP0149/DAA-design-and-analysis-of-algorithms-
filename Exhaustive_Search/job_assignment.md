# Job Assignment

program discription:there are certain number of people so you need to assign works to the persons,that each person get assigned by one
job,so that the minimum money should be paid

```C
#include<stdio.h>
#include<limits.h>
#define n 3
int best_combo[n];
int min_cost=INT_MAX;
int calcost(int cost[n][n],int combo[n]){
int money=0;
for(int i=0;i<n;i++){
 money=money+cost[i][combo[i]];
 }
 return money;
 }
 void swap(int *a,int *b){
  int temp=*a;
  *a=*b;
  *b=temp;
  }
void permutations(int cost[n][n],int combo[n],int st,int end){
 if(st==end){
 int costing;
   costing=calcost(cost,combo);
 if(costing<min_cost){
 min_cost=costing;
 for(int i=0;i<end;i++){
 best_combo[i]=combo[i];
 }
 }
 }
else{
 for(int i=0;i<end;i++){
 swap(&combo[st],&combo[i]);
 permutations(cost,combo,st+1,end);
 swap(&combo[st],&combo[i]);
 }
 }
  }
int main(){
 int cost[n][n]={
   {9,2,7},
   {6,4,3},
   {5,8,1}};
   
 int combo[n];
 for(int i=0;i<n;i++){
  combo[i]=i;
  }
  permutations(cost,combo,0,n);
  printf("the minimum money is =%d\n",min_cost);
  printf("the best combination is");
  for(int i=0;i<n;i++){
  printf("%d",best_combo[i]);
  }
  printf("\n");
  }
```
# complexities

Time complexity:O(n!);//for generating permutations

space complexity:O(n);//n number of persons
   

