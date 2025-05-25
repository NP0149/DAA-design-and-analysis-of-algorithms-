# Kruskal

```
#include<stdio.h>
 #include<stdlib.h>
 int ne,nv;
 //int data[3][20];
 struct edge{
 int src,dest,cost,flag;
 };
 void sort(struct edge e[ne],int ne){
 struct edge t;
 for(int i=0;i<ne;i++){
 for(int j=0;j<ne-i-1;j++){
 if(e[j].cost>e[j+1].cost){
   t=e[j];
   e[j]=e[j+1];
   e[j+1]=t;
   }
   }
   }
   }
   int findunion(int r1,int r2,int data[100][100]){
   int p1=data[1][r1];
   int p2=data[1][r2];
   if(p1!=p2){
   if(data[3][r1]==data[3][r2]){
   data[3][r2]++;
   data[1][r1]=r2;
   }
   else if(data[3][r1]>data[3][r2]){
    data[1][r2]=r1;
    }
    else{
    data[1][r1]=r2;
    }
    return 1;
    }
    else{
    return 0;
    }
    }
 void kruskal(int i,struct edge e[ne],int data[100][100]){
   int r1,r2;
   r1=e[i].src;
   r2=e[i].dest;
   int f=findunion(r1,r2,data);
   if(f==1){
   e[i].flag=1;
   } 
   }
 int main(){
printf("enter no of vertices");
scanf("%d",&nv);
printf("enter no of edges");
scanf("%d",&ne);
struct edge e[ne];
int data[100][100];
for(int i=0;i<ne;i++){
 scanf("%d %d %d",&e[i].src,&e[i].dest,&e[i].cost);
 }
 for(int i=0;i<ne;i++){
   e[i].flag=0;
  }
 sort(e,ne);
 for(int i=0;i<nv;i++){
  data[1][i]=i;
  data[2][i]=i;
  data[3][i]=0;
  }
 for(int i=0;i<ne-1;i++){
  kruskal(i,e,data);
  }
  for(int i=0;i<ne;i++){
   if(e[i].flag==1){
    printf("%d->%d",e[i].src,e[i].dest);
    }
 }
 }
 ```


# Time complexity

ne=number of edges

t(n)=O(nelogne)
