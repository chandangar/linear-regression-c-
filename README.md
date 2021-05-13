#include<bits/stdc++.h>
using namespace std;
float sq(float x)
{
	return x*x;
}
int main()
{
	cout<<"Enter the size of training data: ";
	int m;
	cin>>m;
	vector<int> x;
	vector<int> y;
	cout<<"Enter the value of input and output:\n";
	for(int i=0;i<m;i++)
	{
		int a,b;
		cin>>a>>b;
		x.push_back(a);
		y.push_back(b);
	}
	float rate;
	cout<<"Enter the learning rate:  ";
	cin>>rate;
	float t0,t1;
	t0=t1=0;
	int iter;
	cout<<"Enter the no. of iterations:  ";
	cin>>iter;
	for(int a=1;a<=iter;a++)
	{
		for(int i=0;i<m;i++)
		{
			t0-= rate*(t0+t1*x[i]-y[i])/m;
			t1-= rate*(t0+t1*x[i]-y[i])*x[i]/m;
		}
	}
	float j=0;
	for(int i=0;i<m;i++)
	{
		j+=sq(t0+t1*x[i]-y[i]);
	}
	j/=(2*m);
	cout<<"The cost comes out to be: "<<j<<endl;
	cout<<"Value of t0: "<<t0<<endl;
	cout<<"Value of t1: "<<t1<<endl;
	cout<<"Enter the input value: ";
	int p;
	cin>>p;
	cout<<"The output value is: "<<(t0+t1*p);
	return 0;
}
