# Convex Hull(Brute force)

convex hull is a problem that we need to find the boundary points when set of points given by using all possible combinations

# Approch

find the line equation with the selected two points then substitue every point in that forend equation if the value when 
individual points substituted in it.If the value less than 0 then they are left side of the line segment if value greater tahn 0
then the point is on right .if all the points are right the right count becomes as n-2 ,similarly left also and if the points lies
on the line itself the value becomes zero(collinear points) and then print the points...

```C

#include<stdio.h>
#include<limits.h>
#include<stdlib.h>
struct point{
int x,y;
};
int main(){
struct point p[10];
 int n;
 printf("the number of points in the convex hull");
 scanf("%d",&n);
 printf("enter the points");
 for(int i=0;i<n;i++){
  scanf("%d %d",&p[i].x,&p[i].y);
  }
  for(int i=0;i<n-1;i++){
   for(int j=i+1;j<n;j++){
    int left=0;
  int right=0;
   for(int k=0;k<n;k++){
  int dis=(p[j].x-p[i].x)*(p[k].y-p[i].y)-(p[j].y-p[i].y)*(p[k].x-p[i].x);
   if(dis>0){
   right++;
   }
   else if(dis<0){
   left++;
   }
   else{
   }
   }
    if(left==n-2 || right==n-2 || left==0 || right==0){
    printf("the points on boundary are [%d,%d] & [%d,%d]",p[i].x,p[i].y,p[j].x,p[j].y);
   }
   }
    }
    }
   ```

# Complexities

time complexity:O(n^3);//three loops one in other

space complexity:O(n);//only struct points array used to store n points(input)
