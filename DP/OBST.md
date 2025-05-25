# Optimal binary search tree

```
#include<stdio.h>
 #include<stdlib.h>
 int a[20][2];
 int ob[20][20];
 int w(int i,int j){
 int w=0;
 for(int k=i+1;k<=j;k++){
 w+=a[k][1];
 }
 return w;
 }
 void obst(int a[][2],int n){
 for(int d=1;d<=n;d++){
  for(int i=0;i<=n-d;i++){
  int j=i+d;
  ob[i][j]=999999;
  for(int k=i+1;k<=j;k++){
  int val=ob[i][k-1]+ob[k][j]+w(i,j);
  if(val<ob[i][j]){
 ob[i][j]=val;
  }
  }
  }
  }
  for(int i=0;i<=n;i++){
  for(int j=0;j<=n;j++){
   printf("%d     ",ob[i][j]);
    }
    printf("\n");
    }
    }
    
    
 int main(){
 int n;
 printf("enter number of ele in array");
 scanf("%d",&n);
 printf("enter the ele in matrix");
 for(int i=1;i<=n;i++){
scanf("%d",&a[i][0]);
scanf("%d",&a[i][1]);
}
for(int i=0;i<n;i++){
 for(int j=0;j<2;j++){
  printf("%d ",a[i][j]);
  }
  printf("\n");
}
obst(a,n);
}

 
 
 ```

# Time complexities


t(n)=O(n^3)

