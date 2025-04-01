# Matrix chain multiplication

```
#include<stdio.h>
#include<limits.h>
int main(){
int n=5;
int p[]={5,4,6,2,7};
int m[5][5]={0};
int s[5][5]={0};
int j,min,q;
for(int d=1;d<n-1;d++){
 for(int i=1;i<n-d;i++){
   j=i+d;
   min=INT_MAX;
   for(int k=i;k<=j-1;k++){
 q=m[i][k]+m[k+1][j]+p[i-1]*p[k]*p[j];
 if(q<min){
 min=q;
 s[i][j]=k;
 }
 }
 m[i][j]=min;
 }
 }
 //minimum matrix
for(int i=0;i<n;i++){
 for(int j=0;j<n;j++){
  printf("%d ",m[i][j]);
  }
  printf("\n");
 }
 //k value matrix
 printf("\n the matrix is \n");
 for(int i=0;i<n;i++){
 for(int j=0;j<n;j++){
  printf("%d ",s[i][j]);
  }
  printf("\n");
 }
 
 printf("\nthe minimum number of ways=%d\n",m[1][n-1]);
 }
```
