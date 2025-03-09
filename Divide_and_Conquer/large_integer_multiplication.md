# large inetger multiplication using karatsuba formula

```C
 #include<stdio.h>
#include<math.h>
#include<stdlib.h>
int max(int n1,int n2){
 if(n1>n2)
 return n1;
 else
 return n2;
 }
int largemul(int A,int B,int n){
if(n==1){
return A*B;
}
int d1=(int)pow(10,n/2);
if(d1==0) d1=1;
int a=A/d1;
int b=A%d1;
int c=B/d1;
int d=B%d1;
int ac=largemul(a,c,n/2);
int bd=largemul(b,d,n/2);
int g=largemul((a+b),(c+d),n/2)-ac-bd;
return ac*(int)pow(10,n)+g*d1+bd;
}
int main(){
 int A=1234;
 int B=4567;
 int n1=(int)(log10(A))+1;
 int n2=(int)(log10(B))+1;
 int n=max(n1,n2);
 int result=largemul(A,B,n);
 printf("the result %d ",result);
 }

```
reduced 4 multiplication into 3 multiplications

# complexities

Time complexity:O(n^log2(3));

space complexity:O(nlogn);
