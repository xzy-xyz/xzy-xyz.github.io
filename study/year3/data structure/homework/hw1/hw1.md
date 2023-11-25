## hw1

#### 1.

假设对于常数 $a$ 我们有 $f(n)=O(n\log_an)$，那么根据定义我们可知
$$
\exist~c>0,~~s.t.~f(n)<c\cdot n\log_an~~~~\forall n>>2
$$
接着考虑另一个常数 $b$
$$
\log_a n=\log_ab~\log_bn
$$
因此我们可以把第一个式子表示为
$$
f(n)<c\cdot n\log_ab~\log_bn
$$
令 $c_1=c\cdot \log_ab$，则可以得出 $f(n)=O(n\log_bn)$，即常数 $a$ 取任意大于1的值均等价。

#### 2.

```c++
1.	int sum(int n) {//计算n=1+1×2+1×2×3+……+1×2×……×n
2.	    int s = 0; //初始化最终结果，O(1)
3.	    for(int i = 1; i <= n; ++i) {//全部n个元素循环, O(n)
4.	        int p = 1;//初始化累乘器，O(1)
5.	        for(int j = 1; j <= i; ++j)//循环，O(i)
6.	            p *= j;//累乘O(1)
7.	        s += p;//累加，O(1)
8.	    }
9.	    return s;//返回结果，O(1)
10.	}
```

时间复杂度 $\mathcal{O}(1)+\mathcal{O}(n)\left(\mathcal{O}(1)+\mathcal{O}(i)\mathcal{O}(1)+\mathcal{O}(1)\right)+\mathcal{O}(1)=\mathcal{O}(n^2)$

###### (2)

```c++
1.	int fac(int n) {//计算n=1+1×2+1×2×3+……+1×2×……×n
2.	    int p = 1, s = 0;//初始化累乘器和累加器，O(1)
3.	    for(int i = 1; i <= n; ++i) {//n次循环，O(n)
4.	        p *= i;//累乘，O(1)
5.	        s += p;//累加得到的累乘结果，O(1)
6.	    }
7.	    return s;//返回累加结果，O(1)
8.	}
```

时间复杂度 $\mathcal{O}(1)+\mathcal{O}(n)(\mathcal{O}(1)+\mathcal{O}(1))+\mathcal{O}(1)=\mathcal{O}(n)$

#### 3.

###### (1)

```c++
1.	int f(int n) {//计算斐波那契数列的第n个数
2.	    if (n<=1) return 1;//判断是否到达递归基，是则返回1，O(1)
3.	    else return f(n-1)+f(n-2);//否则递归计算前两项和
4.	}
```

首先把 $\mathrm{f(n)}$ 花费的时间记作 $\mathrm{T(n)}$
$$
\mathrm{T(n)}=
\begin{cases}
1, & \mathrm{n \leq 1}\\
\mathrm{T(n-1)+T(n-2)}+1, & \mathrm{other}
\end{cases}
$$
令 $\mathrm{S(n)=(T(n)+1)/2}$，则
$$
\mathrm{
S(n)=}
\begin{cases}
1, & \mathrm{n \leq 1}\\
\mathrm{S(n-1)+S(n-2)},& \mathrm{other}
\end{cases}
$$
此时可以看到 $\mathrm{S(n)}$ 的递归式与斐波那契数列一致，初始值也一样。根据斐波那契数列的计算公式可知(这里计算公式要根据n=0和n=1时的值进行调整)
$$
\begin{align*}
\mathrm{S(n)}&=\frac{1}{\sqrt{5}}\left(\left(\frac{1+\sqrt{5}}{2}\right)^{n+1}-\left(\frac{1-\sqrt{5}}{2}\right)^{n+1}\right)\\ \\
\mathrm{T(n)}&=2\mathrm{S(n)}-1=\mathcal{O}\left(\left(\frac{1+\sqrt{5}}{2}\right)^{n+1}\right)=\mathcal{O}(2^n)
\end{align*}
$$

###### (2)

```c++
1.	int f(int n) { //计算斐波那契数列第n个数的值
2.	    int a = 1;//初始化第一个数，O(1)
3.	    int b = 1;//初始化第二个数，O(1)
4.	    for (int i = 2; i<=n; ++i) {//从第三个数开始循环，O(n)
5.	        int c = a + b;//计算新的斐波那契数列元素，O(1)
6.	        a = b;//更新a为上一个斐波那契数列元素，O(1)
7.	        b = c;//更新b为当前斐波那契数列元素，O(1)
8.	    }
9.	    return b;//返回第n个斐波那契数列元素，O(1)
10.	} 
```

时间复杂度为 $\mathcal{O}(1)+\mathcal{O}(1)+\mathcal{O}(n)(\mathcal{O}(1)+\mathcal{O}(1)+\mathcal{O}(1))+\mathcal{O}(1)=\mathcal{O}(n)$

###### (3)

假设这里延续上面两题的题设，认为 $\mathrm{fib(1)=1},~~\mathrm{fib(0)=1}$

```c++
1.	float power(double x, int l) {//计算x的l次方
2.	    if (l==0) //如果l是0
3.	        return 1;//直接返回1
4.	    else {
5.	        double temp = power(x, l / 2);//递归计算x的l/2次方
6.	        temp = temp * temp;//temp平方
7.	        if (l % 2 == 1) temp *= x;//如果l是奇数，则再乘上一个x
8.	        return temp;//返回temp的值
9.	    }
10.	}
11.	
12.	int f(int n) {//计算斐波那契数列第n项
13.	    n += 1;//把n加1
14.	    const double a = sqrt(5);//是斐波那契数列计算公式的根号5
15.	    double temp1 = power((1+a)/2, n);//计算公式中的一项
16.	    double temp2 = power((1-a)/2, n);//另一项
17.	    double answer = (temp1-temp2) / a;//计算第n项
18.	    return int(answer + 0.5);//四舍五入到最近的整数返回
19.	}
```

$\mathrm{power(x, l)}$ 函数中，总的时间复杂度是 $\mathcal{O}(\log \mathrm{l})$

函数 $\mathrm{f(n)}$ 中，最主要的就是两次调用 $\mathrm{power(x, l)}$ 函数，其他都是 $\mathcal{O}(1)$ 的时间复杂度，因此 $\mathrm{f}$ 的时间复杂度是 $\mathcal{O}(\log \mathrm{n})$

#### 4.

master theorem 大部分情况可以表示为：将原问题划分为 a 个规模为 n/b 的子任务，任务的划分、解的合并耗时 $\large \mathrm{f(n)}$，那么 $\large{T(n)=a\cdot T(n/b)+\mathcal{O}(f(n))}$

###### a. $T(n)=4T(n/2)+n$

可以看出$\large{a=4，b=2，f(n)=n}$，满足 $\large{\mathrm{f(n)} = \mathcal{O}(n^{log_b a-\epsilon})}$，因此 $\large T(n)=\Theta (n^2)$

###### b. $T(n)=2T(n/4)+\sqrt{(n)}$

$\large{\mathrm{f(n)}=\Theta(n^{\log_ba}\log^kn)}$，其中 $\large k=0$，因此 $\large T(n)=\Theta (n^{\log_ba}\log^{k+1}n)=\Theta (\sqrt{n}\log n)$

###### c. $T(n)=3T(n/4)+n\lg n$

$\large \mathrm{f(n)}=\Omega (n^{\log_ba+\epsilon})=\Omega(n^{\log_4 3}) $，因此 $\large T(n)=\Theta(n\lg n) $

###### d. $T(n)=9T(n/2)+O(n^3)$

$\large \mathrm{f(n)}=\mathcal{O}(n^{\log _ba-\epsilon})=\mathcal{O}(n^{\log_29-\epsilon})$，因此 $\large T(n)=\Theta (n^{\log_29})$

#### 5.

证明：插入在位置 $\large r=1$ 的概率是 $\large 1/n$，在位置 $\large r=1$ 插入需要移动 $\large n$ 个元素，因此时间复杂度是 $\large \mathcal{O}(n)$；

插入在位置 $\large r=2$ 的概率是 $\large 1/n$，在位置 $\large r=2$ 插入需要移动 $\large n-1$ 个元素，因此时间复杂度是 $\large \mathcal{O}(n-1)$

以此类推，插入在位置 $\large r=i$ 的概率是 $\large 1/n$，在位置 $\large r=i$ 插入需要移动 $\large n-i+1$ 个元素，因此时间复杂度是 $\large \mathcal{O}(n-i+1)$

插入在位置 $\large r=n$ 的概率是 $\large 1/n$，在位置 $\large r=n$ 插入时间复杂度是 $\large \mathcal{O}(1)$

那么平均时间复杂度为：
$$
\begin{align*}
E(T(n))&=\frac{1}{n}\left(\mathcal{O}(n)+\mathcal{O}(n-1)+……+\mathcal{O}(1)\right)\\
&=\frac{1}{n}\mathcal{O}\left(\frac{n(n+1)}{2}\right)\\
&=\mathcal{O}\left(\frac{n+1}{2}\right)\\
&=\mathcal{O}(n)
\end{align*}
$$
