## hw2

#### 1.

作用于初始为0的计数器 $n$ 次，对于 $i>\lfloor \log n\rfloor$ 的位来说始终没有影响，但是对 $i \leq \lfloor \log n \rfloor$ 的位置来说，$A[0]$ 会变化 $n$ 次，$A[1]$ 会变化 $\lfloor n/2\rfloor$ 次，以此类推，$A[i]$ 会{变化 $\lfloor n/2^i\rfloor$ 次，因此总的代价满足：
$$
\sum_{i=0}^{\lfloor \log n \rfloor} \lfloor\frac{n}{2^i}\rfloor < n\sum_{i=0}^\infin \frac{1}{2^i}=2n
$$
所以从0开始调用 $n$ 次 INCREMENT 操作的代价是 $\mathcal{O}(n)$ 的，那么平均代价就是：
$$
\mathcal{O}(n)/n = \mathcal{O}(1)
$$

#### 2.