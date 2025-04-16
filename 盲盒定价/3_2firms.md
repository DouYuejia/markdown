# 多公司竞争建模

## 多公司竞争模型：

### 公司

考虑有两家基础属性相同的公司$firm1,firm2$，销售相同属性的商品集合$\{普通商品:r_1,...,r_n;特殊商品:s\}$，$n$种普通商品和特殊商品分别具有价值$v_{r1},...,v_{rn};v_s$。公司的目标是在市场竞争中最大化收益，每个公司可以选择两种销售机制之一：

- 盲盒销售$B(c,p)$：考虑一种特殊情况，有$n$种同质普通商品和1种特殊商品，公司需要设定盲盒价格$c$和抽中特殊商品概率$p$。期望收益为：$REV_B=c\cdot\sum_{r=0}^{n^*-1}\frac{(\frac{np}{1-p}\cdot \sum_{j=1}^{r}\frac{1}{n-n^*+j})+1}{1-(1-p)\frac{r}{n}}\cdot \prod_{l=0}^{r-1}\frac{\frac{n-l}{n}\cdot (1-p)}{1-(1-p)\cdot \frac{l}{n}}+\frac{c}{p}\cdot \prod_{l=0}^{n^*-1}\frac{\frac{n-l}{n}\cdot (1-p)}{1-(1-p)\cdot \frac{l}{n}}\\其中\begin{cases}(n-n^*)V_r-\frac{nc}{1-p}\sum_{j=1}^{n-n^*}\frac{1}{j} \leq 0\\(n-n^*+1)V_r-\frac{nc}{1-p}\sum_{j=1}^{n-n^*+1}\frac{1}{j} \gt 0\\V(0,0)=\sum_{k=0}^{n}\frac{\frac{(1-p)(n-k)\cdot v_r}{n}+p\cdot v_s+p\cdot((n-k)v_r-\frac{cn}{1-p}\sum_{m=1}^{n-k}\frac{1}{m})-c}{1-(1-p)\frac{k}{n}}\prod_{j=0}^{k-1}\frac{(1-p)\frac{n-j}{n}}{1-(1-p)\frac{j}{n}}\gt 0\end{cases}$

  $REV_B$显然随着$n^*$递增，因此始终有$REV_B\geq REV_B|_{n^*=n}=\frac{c}{p}$，可以用来简化分析。

- 分别定价销售$D(c_r,c_s)$：公司需要设定普通商品的价格$c_r$和特殊商品的价格$c_s$。期望收益为：$REV_D=c_s\mathbb{I}(v_s\geq c_s)+nc_r\mathbb{I}(v_r\geq c_r)$

### 消费者

市场中存在两种消费者群体，不同群体对商品的估值不同（*后续考虑风险偏好？*）。消费者在两家公司中选择一家购买，消费者目标是最大化期望效用，因此会选择期望效用最大的公司购买；如果两家公司的期望效用相同，则消费者将随机购买。

- 消费者群体A（总体比例$\alpha$）：估值$\{v_r^A,v_s^A\}$
- 消费者群体B（总体比例$1-\alpha$）：估值$\{v_r^B,v_s^B\}$

消费者对不同销售机制的期望效用：

- 盲盒销售$B(c,p)$：$U_B=V(0,0)=\sum_{k=0}^{n}\frac{\frac{(1-p)(n-k)\cdot v_r}{n}+p\cdot v_s+p\cdot((n-k)v_r-\frac{cn}{1-p}\sum_{m=1}^{n-k}\frac{1}{m})-c}{1-(1-p)\frac{k}{n}}\prod_{j=0}^{k-1}\frac{(1-p)\frac{n-j}{n}}{1-(1-p)\frac{j}{n}}$
- 分别定价销售$D(c_r,c_s)$：$U_D=(v_s-c_s)\mathbb{I}(v_s\geq c_s)+n(v_r-c_r)\mathbb{I}(v_r\geq c_r)$

### 双公司博弈矩阵

|       | $B_2$                             | $D_2$                             |
| ----- | --------------------------------- | --------------------------------- |
| $B_1$ | $(REV_1(B_1,B_2),REV_2(B_1,B_2))$ | $(REV_1(B_1,D_2),REV_2(B_1,D_2))$ |
| $D_1$ | $(REV_1(D_1,B_2),REV_2(D_1,B_2))$ | $(REV_1(D_1,D_2),REV_2(D_1,D_2))$ |

1. $(B_1,B_2)$:即$(B_1(c_1,p_1),B_2(c_2,p_2))$

   消费者A决策：计算$B_1,B_2$下的效用$\begin{cases}U_{B_1}^A=V_{B_1}^A(0,0)\\U_{B_2}^A=V_{B_2}^A(0,0)\end{cases}$,购买决策$\begin{cases}firm1,if& U_{B_1}^A>U_{B_2}^A\\firm2,if& U_{B_1}^A<U_{B_2}^A\\random,if& U_{B_1}^A=U_{B_2}^A\end{cases}$

   消费者B决策：类似的，效用$\begin{cases}U_{B_1}^B=V_{B_1}^B(0,0)\\U_{B_2}^B=V_{B_2}^B(0,0)\end{cases}$

   公司1收益：$REV_1(B_1,B_2)=(\alpha\cdot \mathbb{I}(U_{B_1}^A\gt U_{B_2}^A)+(1-\alpha)\cdot \mathbb{I}(U_{B_1}^B\gt U_{B_2}^B))REV_{B_1}(c_1,p_1)$

   公司2收益：$REV_2(B_1,B_2)=(\alpha\cdot \mathbb{I}(U_{B_1}^A\lt U_{B_2}^A)+(1-\alpha)\cdot \mathbb{I}(U_{B_1}^B\lt U_{B_2}^B))REV_{B_2}(c_2,p_2)$

2. $(B_1,D_2)$:即$(B_1(c_1,p_1),D_2(c_{r2},c_{s2}))$

   消费者A决策：计算$B_1,D_2$下的效用$\begin{cases}U_{B_1}^A=V_{B_1}^A(0,0)\\U_{D_2}^A=(v_s^A-c_{s2})\mathbb{I}(v_s^A\geq c_{s2})+n(v_r^A-c_{r2})\mathbb{I}(v_r^A\geq c_{r2})\end{cases}$

   消费者B决策：类似的，效用$\begin{cases}U_{B_1}^B=V_{B_1}^B(0,0)\\U_{D_2}^B=(v_s^B-c_{s2})\mathbb{I}(v_s^B\geq c_{s2})+n(v_r^B-c_{r2})\mathbb{I}(v_r^B\geq c_{r2})\end{cases}$

   公司1收益：$REV_1(B_1,D_2)=(\alpha\cdot \mathbb{I}(U_{B_1}^A\gt U_{D_2}^A)+(1-\alpha)\cdot \mathbb{I}(U_{B_1}^B\gt U_{D_2}^B))REV_{B_1}(c_1,p_1)$

   公司2收益：$REV_2(B_1,D_2)=(\alpha\cdot \mathbb{I}(U_{B_1}^A\lt U_{D_2}^A)+(1-\alpha)\cdot \mathbb{I}(U_{B_1}^B\lt U_{D_2}^B))REV_{D_2}(c_{r2},c_{s2})$

3. $(D_1,B_2)$:

   公司1收益：$REV_1(D_1,B_2)=(\alpha\cdot \mathbb{I}(U_{D_1}^A\gt U_{B_2}^A)+(1-\alpha)\cdot \mathbb{I}(U_{D_1}^B\gt U_{B_2}^B))REV_{D_1}(c_{r1},c_{s1})$

   公司2收益：$REV_2(D_1,B_2)=(\alpha\cdot \mathbb{I}(U_{D_1}^A\lt U_{B_2}^A)+(1-\alpha)\cdot \mathbb{I}(U_{D_1}^B\lt U_{B_2}^B))REV_{B_2}(c_2,p_2)$

4. $(D_1,D_2)$:

   消费者A决策：计算$D_1,D_2$下的效用$\begin{cases}U_{D_1}^A=(v_s^A-c_{s1})\mathbb{I}(v_s^A\geq c_{s1})+n(v_r^A-c_{r1})\mathbb{I}(v_r^A\geq c_{r1})\\U_{D_2}^A=(v_s^A-c_{s2})\mathbb{I}(v_s^A\geq c_{s2})+n(v_r^A-c_{r2})\mathbb{I}(v_r^A\geq c_{r2})\end{cases}$

   消费者B决策：类似的，效用$\begin{cases}U_{D_1}^B=(v_s^B-c_{s1})\mathbb{I}(v_s^B\geq c_{s1})+n(v_r^B-c_{r1})\mathbb{I}(v_r^B\geq c_{r1})\\U_{D_2}^B=(v_s^B-c_{s2})\mathbb{I}(v_s^B\geq c_{s2})+n(v_r^B-c_{r2})\mathbb{I}(v_r^B\geq c_{r2})\end{cases}$

   公司1收益：$REV_1(D_1,D_2)=(\alpha\cdot \mathbb{I}(U_{D_1}^A\gt U_{D_2}^A)+(1-\alpha)\cdot \mathbb{I}(U_{D_1}^B\gt U_{D_2}^B))REV_{D_1}(c_{r1},c_{s1})$

   公司2收益：$REV_2(D_1,D_2)=(\alpha\cdot \mathbb{I}(U_{D_1}^A\lt U_{D_2}^A)+(1-\alpha)\cdot \mathbb{I}(U_{D_1}^B\lt U_{D_2}^B))REV_{D_2}(c_{r2},c_{s2})$





