# Prims

```
#include<stdio.h>
#include<stdlib.h>
#include<stdbool.h>
#include<limits.h>
#define n 5
int minkey(int key[n],bool mst[n]){
int min=INT_MAX,minindex;
for(int i=0;i<n;i++){
 if(!mst[i] && key[i]<min){
 min=key[i];
 minindex=i;
 }
 }
 return minindex;
 }

void prims(int graph[n][n]){
int parent[n];
int key[n];
bool mst[n];
for(int i=0;i<n;i++){
 parent[i]=-1;
 key[i]=INT_MAX;
 }
 parent[0]=-1;
 key[0]=0;
for(int count=0;count<n-1;count++){
 int u=minkey(key,mst);
 mst[u]=true;
 for(int v=0;v<n;v++){
  if(!mst[v] && graph[u][v]<key[v] && graph[u][v]){
       key[v]=graph[u][v];
       parent[v]=u;
       }
       }
       }
       int totalcost=0;
       for(int i=1;i<n;i++){
       
        printf("%d -> %d\n",i,parent[i]);
        totalcost+=graph[i][parent[i]];
        }
        printf("total cost=%d",totalcost);
        printf(" zero val is %d",parent[0]);
        }
int main(){
 int graph[n][n]={
 {0,2,0,6,0},
 {2,0,3,8,5},
 {0,3,0,0,7},
 {6,8,0,0,9},
 {0,5,7,9,0}
 };
 printf("the minimum cost spanning tree is\n");
 prims(graph);
 return 0;
 }



```

# time complexities

E=number of edges

V=number of vertices

t(n)=O(E+logV)
