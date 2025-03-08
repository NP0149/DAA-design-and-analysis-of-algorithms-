# closest pair(Brute force)
Problem:-when you entered a certain number of points and then you need to find two points which are close to each other among all points
# Approch
as it is in brute force we need to compare all the possible combinations and then find the minimum distance among points and store those points and then print them out
code in C
```C
#include<stdio.h>
#include<math.h>
#include<limits.h>
struct point{
 int x,y;
 };
int main(){
struct point p[10];
int n;
printf("enter the number of points");
scanf("%d",&n);
for(int i=0;i<n;i++){
 scanf("%d%d",&p[i].x,&p[i].y);
 }
  int mindis=INT_MAX;
int a,b,c,d;
for(int i=0;i<n-1;i++){
  for(int j=i+1;j<n;j++){
     int dis=sqrt(pow((p[j].x-p[i].x),2)+pow((p[j].y-p[i].y),2));
     if(dis<mindis){
       mindis=dis;
       a=p[i].x;
       b=p[i].y;
       c=p[j].x;
       d=p[j].y;
       }
       }
       }
      printf("the mindistance is %d",mindis);
      printf("the points [%d,%d]->[%d,%d]",a,b,c,d);
       }
```
#COMPLEXITIES
Time complexity:O(n^2);//loop inside a loop
Space complexity:O(n);//taking n points as input
  
