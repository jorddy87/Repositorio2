#include <iostream>
#include <math.h>
#include <thread>

using namespace std;

int primo(int x);

int circular(int m);

void cuenta();

void cuenta2();

int main()
{
	thread t1(cuenta);
	thread t2(cuenta2);
	t1.join();
	t2.join();

	system("pause");
	return 0;
}

int primo(int x)
{
	int y;
	y = x - 1;
	while (y>1 && x%y != 0)
	{
		y = y - 1;
	}
	if (x == 1 || y == 1)return 1;
	else return 2;
}



int circular(int m)
{
	int resto, aux;
	float c = 0, c2 = 0, z = 0;
	int p = 0;
	int y;
	float d, b = 10;
	y = m;
	y = y / 10;
	while (y != 0)
	{
		y = y / 10;
		c++;
	}
	c2 = c;
	d = pow(b, c);
	while (c != 0)
	{
		resto = m % 10;
		aux = m / 10;
		z = resto*d + aux;
		m = z;
		if (primo(z) == 1)
		{
			p++;
			c--;
		}
		else
		{
			c = 0;
		}
	}
	if (p == c2)
	{
		return 1;
	}
	else
	{
		return 2;
	}
}


void cuenta()
{
	float num = 1;
	int i;
	for (i = 1; i <= 10000; i++)
	{
		if (primo(num) == 1)
		{
			if (circular(num) == 1)
			{
				cout << "es primo circular: " << num << endl;
			}

		}
		num = num + 1;
	}
}


void cuenta2 ()
{
	float num = 10001;
	int i;
	for (i = 1; i <= 1000000; i++)
	{
		if (primo(num) == 1)
		{
			if (circular(num) == 1)
			{
				cout << "es primo circular: " << num << endl;
			}

		}
		num = num + 1;
	}
}