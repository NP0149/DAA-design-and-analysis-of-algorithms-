# floyd warshall

```
#include<stdio.h>
#include<limits.h>
int min(int a,int b){
if(a<b)
return a;
return b;
}
int main(){
int m;
int n=4;
int c[4][4]={{0,3,9999,7},{8,0,2,9999},{5,9999,0,1},{2,9999,9999,0}};
int val,posval;
for(int k=0;k<n;k++){
for(int i=0;i<n;i++){
for(int j=0;j<n;j++){
 c[i][j]=min(c[i][j],c[i][k]+c[k][j]);
 }
 }
 }
 for(int i=0;i<n;i++){
 for(int j=0;j<n;j++){
 printf("%d         ",c[i][j]);
 }
 printf("\n");
 }
 }
 ```
  
