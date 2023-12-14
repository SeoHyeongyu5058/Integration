# Integration<br>

**개요**<br>
* [Rect( )]()<br>
* [MidPoint( )]()<br>
* [trapz( )]()<br>
* [simpson13( )]()<br>
* [simpson38( )]()<br>


<hr>

## Rect( )<br>

```c
double Rect(double x[], double y[], int m);
```
>Parameter<br>
**x[]** : x data set <br>
**y[]** : y data set <br>
**m** : The length of data set <br>

1. myNP.h 안에 선언되어 있다.
2. 다음과 같은 원리를 기반으로 작성되었다.<br>

* Intervals: N  Points=N+1

$$I_O\sim I_{N+1}$$

$$I_O=f(x_O)(x_1-x_0)$$
$$I_k=y_k(x_{k+1}-x_K)$$
$$I=\sum_{k=0}^{N-1}I_k=\sum_{k=0}^{N-1}y_k(x_{k+1}-x_K)$$

<hr>

## Example <br>
```c++
int main()
{
	double x[] = { 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60 };
	double y[] = { 0, 3, 8, 20, 33, 42, 40, 48, 60, 12, 8, 4, 3 };
	int M = sizeof(x) / sizeof(x[0]);

	double X[] = {-3, -2.25, -15, 0.75, 0, 0.75, 1.5, 2.25, 3};
	double Y[] = { 0, 2.1875, 3.75, 4.6875, 5, 4.6875, 3.75, 2.1875, 0 };
	int _M = sizeof(X) / sizeof(X[0]);


	// Exercise 1. Rectangular
	double I_Rect = 0;
	I_Rect = Rect(x, y, M);
	printf("I_Rect = %f\n\n", I_Rect);
}
```

## Output <br>
```c
I_Rect = 1390.000000
```

## Warning
>The length of x and y must be equal<br>
The length of data must be more than 2

## Error Handling
```c
if (sizeof(x) != sizeof(y)) {
	printf("ERROR: length of x and y must be equal\n");
	return;
}

if (m < 3) {
	printf("ERROR: length of data must be more than 2\n");
	return;
}
```
<br>

## MidP0int( )<br>

```c
double MidPoint(double x[], double y[], int m) 
```
>Parameter<br>
**x[]** : x data set <br>
**y[]** : y data set <br>
**m** : The length of data set <br>

1. myNP.h 안에 선언되어 있다.
2. 다음과 같은 원리를 기반으로 작성되었다.<br>



$$I_O\sim I_{N+1}$$

$$I_O=f({{x_O+x_1}\over 2})(x_1-x_0)$$
$$I_k=f({{x_k+x_{k+1}}\over 2})(x_{k+1}-x_k)$$
$$I=\sum_{k=0}^{N-1}I_k=\sum_{k=0}^{N-1}f({{x_k+x_{k+1}}\over 2})(x_{k+1}-x_k)$$
    


<hr>

## Example <br>
```c++
int main()
{
	double x[] = { 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60 };
	double y[] = { 0, 3, 8, 20, 33, 42, 40, 48, 60, 12, 8, 4, 3 };
	int M = sizeof(x) / sizeof(x[0]);

	double X[] = {-3, -2.25, -15, 0.75, 0, 0.75, 1.5, 2.25, 3};
	double Y[] = { 0, 2.1875, 3.75, 4.6875, 5, 4.6875, 3.75, 2.1875, 0 };
	int _M = sizeof(X) / sizeof(X[0]);


	// Exercise 1. Rectangular
    double I_Mid = 0;
    I_Mid = MidPoint(x, y, M);
    printf("I_Mid = %f\n\n", I_Mid);
}
```

## Output <br>
```c
I_Mid = 1390.000000
```

## Warning
>The length of x and y must be equal<br>
The length of data must be more than 3

## Error Handling
```c
if (sizeof(x) != sizeof(y)) 
{
	printf("ERROR: length of x and y must be equal\n");
	return;
}


if (m < 4) 
{
	printf("ERROR: length of data must be more than 3\n");
	return;
}
```
<br>

## trapz( )<br>

```c
double trapz(double x[], double y[], int m);
```
>Parameter<br>
**x[]** : x data set <br>
**y[]** : y data set <br>
**m** : The length of data set <br>

1. myNP.h 안에 선언되어 있다.
2. 다음과 같은 원리를 기반으로 작성되었다.<br>



$$I_O\sim I_{N+1}$$
$$I={1\over 2}(f(a)+f(b))(b-a)$$

$$I=\sum_{k=0}^{N-1}{1\over2}(f(x_k)+f(x_{k+1}))(x_{k+1}-x_k)=h\sum_{k=0}^{N-1}{1\over2}f({{x_k+x_{k+1}}})$$
$$={h\over2}(y_0+y_N)+h\sum_{k=1}^{N-1}y_k$$
    


<hr>

## Example <br>
```c++
int main()
{
	double x[] = { 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60 };
	double y[] = { 0, 3, 8, 20, 33, 42, 40, 48, 60, 12, 8, 4, 3 };
	int M = sizeof(x) / sizeof(x[0]);

	double X[] = {-3, -2.25, -15, 0.75, 0, 0.75, 1.5, 2.25, 3};
	double Y[] = { 0, 2.1875, 3.75, 4.6875, 5, 4.6875, 3.75, 2.1875, 0 };
	int _M = sizeof(X) / sizeof(X[0]);


	// Exercise 1. Rectangular
 	double I_trapz = 0;
	I_trapz = trapz(x, y, M);
	printf("I_trapz = %f\n\n", I_trapz);
}
```

## Output <br>
```c
I_trapz = 1397.500000
```

## Warning
>The length of x and y must be equal<br>
The length of data must be more than 2

## Error Handling
```c
if (sizeof(x) != sizeof(y)) 
{
	printf("ERROR: length of x and y must be equal\n");
	return;
}


if (m < 3) 
{
	printf("ERROR: length of data must be more than 3\n");
	return;
}
```
<br>


## simpson13( )<br>

```c
double trapz(double x[], double y[], int m);
```
>Parameter<br>
**x[]** : x data set <br>
**y[]** : y data set <br>
**m** : The length of data set <br>

1. myNP.h 안에 선언되어 있다.
2. N must be even number
3. 다음과 같은 원리를 기반으로 작성되었다.<br>


$$I_0={h\over 3}[f(x_0)+4f(x_1)+f(x_2)]$$
$$I_1={h\over 3}[f(x_2)+4f(x_3)+f(x_4)]$$
$$\vdots$$
$$I_{{N\over2}-1}={h\over 3}[f(x_{N-2})+4f(x_{N-1})+f(x_N)]$$

$$I=\sum_{k=0}^{{N\over2}-1}I_k={h\over3}(y_0+y_N)+{2h\over3}\sum_{k=1}^{{N\over2}-1}y_{2k}+{4h\over3}\sum_{k=1}^{{N\over2}}y_{2k-1}$$
    


<hr>

## Example <br>
```c++
int main()
{
	double X[] = {-3, -2.25, -15, 0.75, 0, 0.75, 1.5, 2.25, 3};
	double Y[] = { 0, 2.1875, 3.75, 4.6875, 5, 4.6875, 3.75, 2.1875, 0 };
	int _M = sizeof(X) / sizeof(X[0]);



	double I_simpson13 = 0;
	I_simpson13 = simpson13(X,Y,_M);
	printf("I_simpson13  = %f\n\n", I_simpson13);
}
```

## Output <br>
```c
I_simpson13  = 20.000000
```

## Warning
>The length of x and y must be equal<br>
The length of data must be more than 3

## Error Handling
```c
if (sizeof(x) != sizeof(y)) 
{
	printf("ERROR: length of x and y must be equal\n");
	return;
}


if (m < 3) 
{
	printf("ERROR: length of data must be more than 3\n");
	return;
}
```
<br>

## simpson38( )<br>

```c
double simpson38(double x[], double y[], int m);
```
>Parameter<br>
**x[]** : x data set <br>
**y[]** : y data set <br>
**m** : The length of data set <br>

1. myNP.h 안에 선언되어 있다.
2. N must be odd number
3. 다음과 같은 원리를 기반으로 작성되었다.<br>


$$I_0={3h\over 8}[f(x_0)+3f(x_1)+3f(x_2)f(x_3)]$$
$$I_1={3h\over 8}[f(x_3)+3f(x_4)+3f(x_5)+f(x_6)]$$
$$\vdots$$
$$I_{{N\over3}-1}={3h\over 8}[f(x_{N-3})+3f(x_{N-2})+3f(x_{N-1})+f(x_N)]$$

$$I=\sum_{k=0}^{{N\over3}-1}I_k={3h\over8}(y_0+y_N)+{9h\over8}\sum_{k=1}^{{N\over3}}(y_{3k-2}+y_{3k-1})+{6h\over8}\sum_{k=1}^{{N\over3}-1}y_{3k}$$
    


<hr>

## Example <br>
```c++
int main()
{
	double X[] = {-3, -2.25, -15, 0.75, 0, 0.75, 1.5, 2.25, 3};
	double Y[] = { 0, 2.1875, 3.75, 4.6875, 5, 4.6875, 3.75, 2.1875, 0 };
	int _M = sizeof(X) / sizeof(X[0]);


	double I_simpson38 = 0;
	I_simpson38 = simpson38(X, Y, _M);
	printf("I_simpson38  = %f\n\n", I_simpson38);
}
```

## Output <br>
```c
I_simpson38  = 13.183594
```

## Warning
>The length of x and y must be equal<br>
The length of data must be more than 4

## Error Handling
```c
if (sizeof(x) != sizeof(y)) 
{
	printf("ERROR: length of x and y must be equal\n");
	return;
}


if (m < 4) 
{
	printf("ERROR: length of data must be more than 3\n");
	return;
}
```
<br>
