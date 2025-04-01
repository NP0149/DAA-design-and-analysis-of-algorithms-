# Binomial Coefficient

```
#include<stdio.h>
#include<stdlib.h>
int a[20][20];
void printpascal(int n){
 for(int i=0;i<n;i++){
 for(int j=0;j<=i;j++){
  if(j==0 || j==i){
a[i][j]=1;
 }
 else{
 a[i][j]=a[i-1][j-1]+a[i-1][j];
 }
  printf("%d",a[i][j]);
  }
  printf("\n");
  }
  }
int main(){
int n;
  printf("enter n");
  scanf("%d",&n);
  printpascal(n);
  }
```
