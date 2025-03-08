# Travelling Sales man problem

this problem mainly asks to find there is a sales man and he need to cover all the cities but in least distance covered and need 
to get back to the same position

# Approach

generate all the possible permutations consider it as route array then pass that array and compare the distance which gives
the shortest distance store the route and print

```C
#include<stdio.h>
#include<stdlib.h>
#include<limits.h>
#define n 3
int min_dis=INT_MAX;
int best_route[n];
int find_dis(int dis[n][n],int route[]){
int cost=0;
for(int i=0;i<n;i++){
cost=cost+dis[route[i+1]][route[i]];
}
cost=cost+dis[route[n-1]][route[0]];
return cost;
}
void swap(int* a,int* b){
 int temp=*a;
 *a=*b;
 *b=temp;
}
void permutations(int dis[n][n], int route[],int st,int end){
 if(st==end){
  int d;
  d=find_dis(dis,route);
  if(d<min_dis){
min_dis=d;
for(int i=0;i<n;i++){
 best_route[i]=route[i];
 }
 }
 }
 else{
 for(int i=st;i<end;i++){
  swap(&route[st],&route[i]);
  permutations(dis,route,st+1,end);
  swap(&route[st],&route[i]);
  }
  }
  }
int main(){
 int dis[n][n];
 printf("enter the array elements");
 for(int i=0;i<n;i++){
  for(int j=0;j<n;j++){
   scanf("%d",&dis[i][j]);
   }
   }
   int route[n];
   for(int i=0;i<n;i++){
    route[i]=i;
    }
   int st=0;
   int end=n;
   permutations(dis,route,st,end);
   printf("the minimum distance is %d\n",min_dis);
   printf("the best route\n");
   for(int i=0;i<n;i++){
    printf("%d ",best_route[i]);
    }
    }
   ```

# Complexities

Time complexity:O(n^2);

space complexity:O(n^2);

