#include<iostream>
#include<cmath>
using namespace std;
int n,x[200];//n为皇后数，x[i]为第i个皇后的列数 

bool check(int k)//检查第K个皇后是否满足要求 
{
	for(int i=1;i<k;i++)
	{
	    if(abs(x[i]-x[k])==abs(i-k)||x[i]==x[k])return false;	
	} 
	return true;
}

void output(int n)//输出所有的n皇后问题的解 
{
	for(int i=1;i<=n;i++)
	{
	  cout<<x[i]<<' ';	
	}
	cout<<endl;
}

void backdate(int n)
{
	int k=1;//k表示第k个皇后,第k行 
	x[1]=0;
	while(k>0)
	{
		x[k]++;//重新确定第K个皇后的位置
		while((x[k]<=n)&&(check(k)==false))
		{
			x[k]++;
		}//逐列搜索
		if(x[k]<=n)//此时 第K个皇后满足要求
		{
			if(k==n)
			{
				output(n);
			}
			else//寻找下一个皇后 
			{
				k++;
			    x[k]=0;
			}
		 
		}
		else//此时 第K个皇后不满足要求，需要重新确定前一个皇后的位置 
		{
			k--; 
		}
	} 
} 

int main()
{
	cin>>n;
	backdate(n); 
} 
