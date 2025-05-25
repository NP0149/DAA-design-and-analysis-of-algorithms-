# Knapsack 

```
#include<stdio.h>
#include<limits.h>
#include<stdlib.h>
#define n 4
int b[20][20],wt[n],pr[n],include[n];
typedef struct{
int wt,pr;
}details;
int compare(const void *a,const void *b){
int x=((details*)a)->wt;
int y=((details*)b)->wt;
return (x>y)-(x<y);
}
int max(int a,int b){
 if(a>b){
  return a;
  }
  else{
  return b;
  }
  }
int knap(details e[n],int kw){
qsort(e,n,sizeof(details),compare);
for(int i=0;i<n;i++){
 printf("%d->%d\n",e[i].wt,e[i].pr);
 }
 for(int i=0;i<=n;i++){
  for(int j=0;j<=kw;j++){
    if(i==0 || j==0){
 b[i][j]=0;
 }
 else if(j>=e[i-1].wt){
  b[i][j]=max(b[i-1][j],(b[i-1][j-e[i-1].wt]+e[i-1].pr));
  }
  else{
  b[i][j]=b[i-1][j];
  }
  }
  }
  for(int i=0;i<=n;i++){
   for(int j=0;j<=kw;j++){
     printf("%d ",b[i][j]);
  }
  printf("\n");
  }
 printf("\nItems included in the knapsack:\n");
    int i = n, j = kw;
    while (i > 0 && j > 0) {
        if (b[i][j] != b[i - 1][j]) {
            // Item i-1 is included
            printf("Item %d (wt = %d, pr = %d)\n", i - 1, e[i - 1].wt, e[i - 1].pr);
            j = j - e[i - 1].wt;
        }
        i--;
    }
  return b[n][kw];
  }
int main(){
int kw;
details e[n];
for(int i=0;i<n;i++){
 scanf("%d %d",&e[i].wt,&e[i].pr);
 }
 printf("enter knap weight");
 scanf("%d",&kw);
 int totalpr=knap(e,kw);
 printf("the total profit is %d ",totalpr);
 }


```

# time complexity

n=number of items

W=max weight the bag can hold

t(n)=O(nW)
