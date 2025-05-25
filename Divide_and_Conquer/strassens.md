# strassens multiplication

```
#include<stdio.h>
#define MAX 100

//Strassen's matrix multiplication 
//2 power matrices: 2,4,8,16,32

void add(int a[MAX][MAX],int b[MAX][MAX],int c[MAX][MAX],int n)
{
	for(int i=0;i<n;i++)for(int j=0;j<n;j++)c[i][j]=a[i][j]+b[i][j];
}

void sub(int a[MAX][MAX],int b[MAX][MAX],int c[MAX][MAX],int n)
{
	for(int i=0;i<n;i++)for(int j=0;j<n;j++)c[i][j]=a[i][j]-b[i][j];
}


void strassen(int a[MAX][MAX],int b[MAX][MAX],int c[MAX][MAX],int n)
{
	if(n==2)
	{
		
		
		int d1 = (a[0][0] + a[1][1]) * (b[0][0] + b[1][1]);
		int d2 = (a[1][0] + a[1][1]) * b[0][0];
		int d3 = a[0][0] * (b[0][1] - b[1][1]);
		int d4 = a[1][1] * (b[1][0] - b[0][0]);
		int d5 = (a[0][0] + a[0][1]) * b[1][1];
		int d6 = (a[1][0] - a[0][0]) * (b[0][0] + b[0][1]);
		int d7 = (a[0][1] - a[1][1]) * (b[1][0] + b[1][1]);
		
		
		c[0][0]=d1+d4-d5+d7;
		c[0][1]=d3+d5;
		c[1][0]=d2+d4;
		c[1][1]=d1+d3-d2+d6;
		
		
	}
	else
	{
		//divide it into submatrix 
		int a00[MAX][MAX],a01[MAX][MAX],a10[MAX][MAX],a11[MAX][MAX],b00[MAX][MAX],b01[MAX][MAX],b10[MAX][MAX],b11[MAX][MAX];
		
		
		int temp1[MAX][MAX],temp2[MAX][MAX];//if two matrices are added or sub or mul ==temp matrices are used to store the results;
		
		
		
		int newsize=n/2;
		
		for(int i=0;i<newsize;i++)
		{
			for(int j=0;j<newsize;j++)
			{
				a00[i][j]=a[i][j];
				a01[i][j]=a[i][j+newsize];
				a10[i][j]=a[i+newsize][j];
				a11[i][j]=a[i+newsize][j+newsize];
				
				b00[i][j]=b[i][j];
				b01[i][j]=b[i][j+newsize];
				b10[i][j]=b[i+newsize][j];
				b11[i][j]=b[i+newsize][j+newsize];
			}
		}
		
		int d1[MAX][MAX],d2[MAX][MAX],d3[MAX][MAX],d4[MAX][MAX],d5[MAX][MAX],d6[MAX][MAX],d7[MAX][MAX];
		
		//int d1 = (a[0][0] + a[1][1]) * (b[0][0] + b[1][1]);
		
		add(a00,a11,temp1,newsize);
		add(b00,b11,temp2,newsize);
		strassen(temp1,temp2,d1,newsize);
		
		//int d2 = (a[1][0] + a[1][1]) * b[0][0];
		
		add(a10,a11,temp1,newsize);
		strassen(temp1,b00,d2,newsize);
		
		//int d3 = a[0][0] * (b[0][1] - b[1][1]);
		
		sub(b01,b11,temp1,newsize);
		strassen(a00,temp1,d3,newsize);
		
		//int d4 = a[1][1] * (b[1][0] - b[0][0]);
		
		sub(b10,b00,temp1,newsize);
		strassen(a11,temp1,d4,newsize);
		
		//int d5 = (a[0][0] + a[0][1]) * b[1][1];
		
		add(a00,a01,temp1,newsize);
		strassen(temp1,b11,d5,newsize);
		
		//int d6 = (a[1][0] - a[0][0]) * (b[0][0] + b[0][1]);
		
		sub(a10,a00,temp1,newsize);
		add(b00,b01,temp2,newsize);
		strassen(temp1,temp2,d6,newsize);
		
		//int d7 = (a[0][1] - a[1][1]) * (b[1][0] + b[1][1]);
		
		sub(a01,a11,temp1,newsize);
		add(b10,b11,temp2,newsize);
		strassen(temp1,temp2,d7,newsize);
		
		int c00[MAX][MAX],c01[MAX][MAX],c10[MAX][MAX],c11[MAX][MAX];
		
		
		
		// c00 = d1 + d4 - d5 + d7
		add(d1, d4, temp1, newsize);
		sub(temp1, d5, temp2, newsize);
		add(temp2, d7, c00, newsize);

		// c01 = d3 + d5
		add(d3, d5, c01, newsize);

		// c10 = d2 + d4
		add(d2, d4, c10, newsize);

		// c11 = d1 + d3 - d2 + d6
		add(d1, d3, temp1, newsize);
		sub(temp1, d2, temp2, newsize);
		add(temp2, d6, c11, newsize);

		
		//join c 's to form c matrix
		
		for(int i=0;i<newsize;i++)
		{
			for(int j=0;j<newsize;j++)
			{
				c[i][j]=c00[i][j];
				c[i][j+newsize]=c01[i][j];
				c[i+newsize][j]=c10[i][j];
				c[i+newsize][j+newsize]=c11[i][j];
			}
		}
		
	}
}
void main()
{
	int n;
	printf("enter size of matrix");
	scanf("%d",&n);
	
	int a[MAX][MAX],b[MAX][MAX],c[MAX][MAX];
	for(int i=0;i<n;i++)for(int j=0;j<n;j++)scanf("%d",&a[i][j]);
	for(int i=0;i<n;i++)for(int j=0;j<n;j++)scanf("%d",&b[i][j]);
	
	strassen(a,b,c,n);
	
	for(int i=0;i<n;i++)
		{
		for(int j=0;j<n;j++)printf("%d\t",c[i][j]);
		printf("\n");
		}
}

/*enter size of matrix4
7 14 15 6
4 8 12 3
14 21 6 9
13 7 6 4
5 7 14 2
8 16 4 9
13 6 8 4
6 3 2 4
378	381	286	224	
258	237	190	140	
370	497	346	277	
223	251	266	129	*/

/*
enter size of matrix8
1 0 2 1 3 2 4 1
4 3 2 1 0 1 2 3
1 1 1 1 1 1 1 1
2 3 4 5 6 7 8 9
9 8 7 6 5 4 3 2
0 1 0 1 0 1 0 1
5 5 5 5 5 5 5 5
1 2 3 4 5 6 7 8
1 2 3 4 5 6 7 8
8 7 6 5 4 3 2 1
1 3 5 7 9 11 13 15
15 13 11 9 7 5 3 1
1 1 1 1 1 1 1 1
2 2 2 2 2 2 2 2
3 3 3 3 3 3 3 3
4 4 4 4 4 4 4 4
41	44	47	50	53	56	59	62	
65	68	71	74	77	80	83	86	
35	35	35	35	35	35	35	35	
185	182	179	176	173	170	167	164	
200	203	206	209	212	215	218	221	
29	26	23	20	17	14	11	8	
175	175	175	175	175	175	175	175	
150	147	144	141	138	135	132	129


enter size of matrix8
1 2 3 4 5 6 7 8
8 7 6 5 4 3 2 1
1 3 5 7 2 4 6 8
8 6 4 2 7 5 3 1
2 4 6 8 1 3 5 7
7 5 3 1 8 6 4 2
1 4 7 2 5 8 3 6
6 3 8 5 2 7 1 4
8 1 6 3 5 7 2 4
4 8 2 6 1 3 7 5
5 2 7 4 3 6 8 1
1 6 3 8 7 2 4 5
7 3 4 5 8 1 6 2
2 5 8 1 6 4 3 7
3 7 1 2 4 5 5 8
6 4 5 7 2 8 1 3
151	173	158	160	164	167	147	169	
173	151	166	164	160	157	177	146	
140	177	154	179	152	172	153	163	
184	147	170	145	172	152	171	152	
140	175	154	185	148	172	159	158	
184	149	170	139	176	152	165	157	
157	159	186	152	156	165	169	149	
160	140	198	155	162	176	159	145
*/

```

# time complexity

T(n)=O(n^log2​7)≈O(n^2.81)
