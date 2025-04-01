# Multistage Graph

# Approach

just take a matrix fill it if there is vertex and then take cost 1-D array ,path 1-D array,destination 1-D array
claculate all the distances from that point to the last stage and then assign minimum value to the cost array and k value to destination 
array 

```
#include<stdio.h>
#include<limits.h>
int main(){
 int stages=4,min;
 int n=9;
 int cost[9],d[9],path[9];
 int c[9][9];
 int m,val,posval;
 //matrix intialisation if there is edge assign that value else assign as 0
  for(int i=0;i<n;i++){
 printf("enter how many insertion %d are there",i);
 scanf("%d",&m);
 for(int j=0;j<n;j++){
 c[i][j]=0;
 for(int k=0;k<m;k++){
  printf("enter the j value");
  scanf("%d",&val);
  printf("enter the actual val at pos");
  scanf("%d",&posval);
  c[i][val]=posval;
  }
  break;
  }
  }
cost[n-1]=0;//because it is the actual destination 
for(int i=n-2;i>=1;i--){
min=3456789;
  for(int k=i+1;k<n;k++){
   if(c[i][k]!=0 && c[i][k]+cost[k]<min){
   min=c[i][k]+cost[k];
   d[i]=k;
   }
   }
   cost[i]=min;
   }
   for(int i=0;i<n;i++){
  printf("%d ",cost[i]);
  }
  printf("\ndestination matrix\n");
   for(int i=0;i<n;i++){
  printf("%d ",d[i]);
  }
  printf("\n path is \n");
   path[stages]=n-1;
 path[1]=1;
  for(int i=2;i<stages;i++){
 path[i]=d[path[i-1]];
  }
  for(int i=1;i<=stages;i++){
   printf("%d->",path[i]);
   }
   }
  ```

# Complexity Analysis

Time complexity:O(N^2);

Space complexity:O(1);
