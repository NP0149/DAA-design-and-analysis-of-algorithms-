# String matching(Brute Force)

we need to check whether the substring is present in string

# Approach

compare all the main string characters with the substring ,set flag to 0 if string matches set the flag to 1 and then return

```C
#include<stdio.h>
#include<string.h>
int issubstring(char s1[],char s2[]){
int n=strlen(s1);
int m=strlen(s2);
for(int i=0;i<n-m;i++){
int flag=1;
  for(int j=0;j<m;j++){
   if(s2[j]!=s1[i+j]){
    flag=0;
    break;
    }
    }
    if(flag==1)
    return 1;
    }
    return 0;
    }
int main(){
 char s1[20];
 char s2[20];
 printf("enter main string");
 scanf("%s",s1);
  printf("enter sub string");
 scanf("%s",s2);
 int s=issubstring(s1,s2);
 if(s==1){
 printf("the substring is in string\n");
 }
 else{
 printf("the substring is not in string\n");
 }
 }
```
# complexities

Time complexity:O(n x m);

Space complexity:O(1);//because nothing is taken dynamically
