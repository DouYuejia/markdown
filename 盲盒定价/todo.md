$&REV =E(0,0)\cdot c\\&=c\cdot\sum_{r=0}^{n^*-1}\frac{(\frac{np}{1-p}\cdot \sum_{j=1}^{r}\frac{1}{n-n^*+j})+1}{1-(1-p)\frac{r}{n}}\cdot \prod_{l=0}^{r-1}\frac{\frac{n-l}{n}\cdot (1-p)}{1-(1-p)\cdot \frac{l}{n}}+\frac{c}{p}\cdot \prod_{l=0}^{n^*-1}\frac{\frac{n-l}{n}\cdot (1-p)}{1-(1-p)\cdot \frac{l}{n}}\\&其中\begin{cases}(n-n^*)V_r-\frac{nc}{1-p}\sum_{j=1}^{n-n^*}\frac{1}{j} \leq 0\\(n-n^*+1)V_r-\frac{nc}{1-p}\sum_{j=1}^{n-n^*+1}\frac{1}{j} \gt 0\\V(0,0)=\sum_{k=0}^{n}\frac{\frac{(1-p)(n-k)\cdot v_r}{n}+p\cdot v_s+p\cdot((n-k)v_r-\frac{cn}{1-p}\sum_{m=1}^{n-k}\frac{1}{m})-c}{1-(1-p)\frac{k}{n}}\prod_{j=0}^{k-1}\frac{(1-p)\frac{n-j}{n}}{1-(1-p)\frac{j}{n}}\gt 0\end{cases}$





如果仿真结果成立，REV最大的情况一定是$c/p$。因此，寻找最大的(p,c)等于：

$\max_{c,p} c/p\\s.t.\sum_{k=0}^{n}\frac{\frac{(1-p)(n-k)\cdot v_r}{n}+p\cdot v_s+p\cdot((n-k)v_r-\frac{cn}{1-p}\sum_{m=1}^{n-k}\frac{1}{m})-c}{1-(1-p)\frac{k}{n}}\prod_{j=0}^{k-1}\frac{(1-p)\frac{n-j}{n}}{1-(1-p)\frac{j}{n}}\gt 0$