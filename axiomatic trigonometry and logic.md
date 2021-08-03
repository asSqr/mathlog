本稿は (完全な趣味で) 三角関数を公理的に定義しているものの，内容は高校数学の至って初歩的なものですので，同じ初学者の方以外にはあまり意味はないように思います．

## はじめに
高校数学を学ばれている社会人の方から，三角関数の方程式から三角形の形状を決定する問題に関して，「誤答をしてしまったがなぜ間違っているのか分からない」という趣旨の質問を受けました．本稿では，三角関数を公理的に定義し，そこから高等学校で習うような初等的な公式を導出した後，論理をきちんと意識して「寄せられた解答がなぜ誤答なのか？」を考えていきたいと思います．というのも，高校数学の問題だけを解いてきた方にとって，「一体何を前提に議論しているのか？」「何気なく用いている概念の定義は何か？」「論理 (特に同値性) とは何か？」は必ずしも明らかではなく，私が口頭でいくら指導しても伝わりきらないことがあると思うからです．その方は今後大学数学を学ぶことを志しておられるので，少々初学者には難しいかもしれませんが，(妥協はありますが) 私なりに「前提を疑う」ことを実行してみた痕跡を記してみようと思います．

今回はその 1 として，三角関数を公理的に構築してみようと思います (その 1 でこんなにやったらその 2 については書くことがあまりなくなりそうですが)

## 三角関数を定義する
mathlog の使い方がわかっておらず，番号がずれてしまうので前提としている解析の基礎知識等は下の方にまとめました．適宜ご参照ください．

&&&def 三角関数の公理
$p$ を正の実数とし，$S,\ C : \mathbb{R} \rightarrow \mathbb{R}$ を以下の 3 条件を満たすものとする：

1. $\forall x, y \in \mathbb{R}. C(x-y) = C(x)C(y) + S(x)S(y),$
2. $S(p) = 1,$
3. $\forall x \in [0, p]. S(x) \geq 0.$
&&&

この定義から，$S,\ C$ が一意的に定まる連続関数であることを示すために，種々の事実を示します．以下で用いられる $x, y$ は特に断りがなければ任意の実数とします．

&&&lem
$C(0)=1,\ S(0)=0.$
&&&


&&&prf
定義 1 1. より，
$C(0) = C(p-p) = (C(p))^2+(S(p))^2 = (C(p))^2+1$ なので， $C(0) \geq 1$．
一方， 同様に $C(0) = C(0-0) = (C(0))^2 + (S(0))^2 \geq (C(0))^2$ と上の議論から $C(0) > 0$ を合わせて，両辺 $C(0)$ で割ると $1 \geq C(0)$．
ゆえに，$C(0)=1$ である． 合わせて $S(0) = 0$ がわかる．
&&&

&&&lem
$C(-x) = C(x).$
&&&

&&&prf
定義 1 1. と補題 1 より，
$C(-x) = C(0-x) = 1 \cdot C(x)+0 \cdot S(x) = C(x).$
&&&

&&&lem
R1. $(C(x))^2+(S(x))^2=1,$
R2. $\forall x \in [0, p]. 0 \leq S(x) \leq 1.$
&&&

&&&prf
i. 定義 1 1. より，$1 = C(0) = C(x-x) = (C(x))^2+(S(x))^2$.
ii. 定義 1 3. と i. を合わせて，明らか．
&&&

&&&lem
$C(p) = 0$.
&&&

&&&prf
定義 1 1., 3. より，$1 = (C(p))^2+(S(p))^2 = (C(p))^2 + 1$ なので， $C(p) = 0$ である．
&&&

&&&lem
(a) $C(p-x) = S(x)$,
(b) $S(p-x) = C(x)$,
(c) $S\left(\dfrac{p}{2}\right) = C\left(\dfrac{p}{2}\right)$,
(d) $\forall x \in [0, p]. 0 \leq C(x) \leq 1$.
&&&

&&&prf
(a) 定義 1 1. と 補題 4 より，$C(p-x) = 0 \cdot C(x) + 1 \cdot S(x) = C(x)$.
(b) (a) において $x$ を $p-x$ に置き換えることで示される．
(c) (a) において $x=\frac{p}{2}$ の場合である．
(d) $x \in [0, p]$ において，$C(x) = S(p-x)$ であり，補題 3 ii. から従う．
&&&

&&&lem
(a) $S(x+y) = S(x)C(y) + C(x)S(y)$,
(b) $S(2x) = 2S(x)C(x)$,
(c) $S(2p) = 0$.
&&&

&&&prf
(a) 補題 5 (a), (b) より，$S(x+y) = C((p-x)-y) = C(p-x)C(y) + S(p-x)S(y) = S(x)C(y) + C(x)S(y)$.
(b) (a) において $y = x$ とした場合である．
(c) (b) において， $x = p$ とすると，補題 4 より従う．
&&&

&&&lem
(a) $2\left(C\left(\dfrac{p}{2}\right)\right)^2 = 2\left(S\left(\dfrac{p}{2}\right)\right)^2 = 1$,
(b) $S\left(\dfrac{p}{2}\right) = C\left(\dfrac{p}{2}\right) = \dfrac{\sqrt{2}}{2}$.
&&&

&&&prf
(a) 補題 3 i. と補題 5 (c) から従う．
(b) (a) と補題 3 ii. および 補題 5 (d) から従う．
&&&

&&&lem
$S\left(-\dfrac{p}{2}\right) = -S\left(\dfrac{p}{2}\right) = -\dfrac{\sqrt{2}}{2}$.
&&&

&&&prf
補題 1, 補題 6 (a), 補題 7 (b), 補題 2より，$0 = S(0) = S\left(\dfrac{p}{2}+\left(-\dfrac{p}{2}\right)\right) = S\left(\dfrac{p}{2}\right)C\left(-\dfrac{p}{2}\right)+C\left(\dfrac{p}{2}\right)S\left(-\dfrac{p}{2}\right)\\=S\left(\dfrac{p}{2}\right)\dfrac{\sqrt{2}}{2}+\dfrac{\sqrt{2}}{2}S\left(-\dfrac{p}{2}\right).$
よって， $S\left(-\dfrac{p}{2}\right) = -S\left(\dfrac{p}{2}\right)$ であり，補題 7 (b) から，示された．
&&&

&&&lem
$S(-p) = -1$.
&&&

&&&prf
補題 6 (b), 補題 2, 補題 7, 補題 8 より，$S(-p) = 2S\left(-\dfrac{p}{2}\right)C\left(-\dfrac{p}{2}\right) = -1$.
&&&

&&&lem
$C(2p) = -1$.
&&&

&&&prf
補題 9 と補題5 (b) より従う．
&&&

&&&lem
$S(-x) = -S(x)$.
&&&

&&&prf
補題 5 (a), 定義 1 1. より，
$S(-x) = C(p-(-x)) = C(-p-x) = C(-p)C(x) + S(-p)S(x)$.
さらに，補題 2, 補題 4, 補題 9 より，
$S(-x) = -S(x)$. 
&&&

&&&lem
(a) $C(x+y) = C(x)C(y) - S(x)S(y)$,
(b) $C(2x) = (C(x))^2 - (S(x))^2 = 2(C(x))^2-1$,
(c) $\dfrac{C(x)+1}{2} = \left(C\left(\dfrac{x}{2}\right)\right)^2$.
&&&

&&&prf
(a) 定義 1 1., 補題 2, 補題 11 より，$C(x+y) = C(x-(-y)) = C(x)C(-y)+S(x)S(-y) = C(x)C(y)-S(x)S(y)$.
(b) (a) において $y=x$ とし，補題 3 i. と合わせて示される．
(c) (b) において $x$ を $\frac{x}{2}$ と置き換えた場合に相当する．
&&&

&&&lem
$S(x-y) = S(x)C(y)-C(x)S(y)$.
&&&

&&&prf
補題 6 (a), 補題 2, 補題 11 より．$S(x-y) = S(x+(-y)) = S(x)C(-y)+C(x)S(-y) = S(x)C(y) - C(x)S(y)$.
&&&

&&&lem
(a) $S(p+x) = C(x)$,
(b) $C(p+x) = -S(x)$,
(c) $S(2p+x) = -S(x)$,
(d) $C(2p+x) = -C(x)$,
(e) $S(4p+x) = S(x)$,
(f) $C(4p+x) = C(x)$.
&&&

&&&prf
(a) 補題 6 (a), 定義 1 2., 補題 4 より，$S(p+x) = 1 \cdot C(x)+0 \cdot S(x) = C(x)$.
(b) 補題 12 (a), 定義 1 2., 補題 4 より，$C(p+x) = 0 \cdot C(x) - 1 \cdot S(x) = -S(x)$.
(c) 補題 6 (a), 補題 6 (c), 補題 10 より，$S(2p+x) = 0 \cdot C(x) + (-1) \cdot S(x) = -S(x)$.
(d) 補題 12 (a), 補題 6 (c), 補題 10 より，$C(2p+x) = (-1) \cdot C(x)-0 \cdot S(x) = -C(x)$.
(e) 補題 6 (a), 補題 6 (b), (c), 補題 10, 補題 12 (b) より，$S(4p+x) = 0 \cdot C(x)+1 \cdot S(x) = S(x)$.
(e) 補題 12 (a), 補題 6 (b), (c), 補題 10, 補題 12 (b) より，$C(4p+x) = 1 \cdot C(x) - 0 \cdot S(x) = C(x)$.
&&&

補題 2, 11, 14 より， $S,\ C$ は $[0, p]$ の区間内で唯一に決定すれば，全体でも唯一に決定されることがわかります．また，補題 14 (e), (f) は特に周期性を表しています．以降で唯一性を示しますが，登場する $x$ は全て $[0, p]$ の区間に制限されるものとし，それに伴い $S,\ C$ の値域は $[0, 1]$ となります．

&&&lem
(a) $C$ は $[0, p]$ 上の単調非増加関数である．
(b) $S$ は $[0, p]$ 上の単調非減少関数である．
&&&

&&&prf
(a) 補題 3 (b), 補題 5 (d), 補題 12 (a) より， $C(x+y) \leq C(x)$.
(b) 補題 5(a), 補題 15 (a) より，従う．
&&&

&&&lem
任意の定数 $c$ に対し，$C(x) \geq 1-c$ ならば$C\left(\dfrac{x}{2}\right) \geq 1 - \dfrac{c}{2}$.
&&&

&&&prf
$C$ の値域は $[0, 1]$ であることと，補題 12 (c) より，$C\left(\dfrac{x}{2}\right) \geq \left(C\left(\dfrac{x}{2}\right)\right)^2 = \dfrac{1+C(x)}{2} \geq \dfrac{1+(1-c)}{2} \geq 1-\dfrac{c}{2}$.
&&&

&&&lem
$\displaystyle\lim_{n \to \infty} C\left(\dfrac{p}{2^n}\right) = 1.$
&&&

&&&prf
補題 4 より，$C(p) = 0 \geq 1-1$ であるから，補題 16 から帰納的に $C\left(\dfrac{p}{2^n}\right) \geq 1-\dfrac{1}{2^n}$ が任意の正整数 $n$ について示される．一方 $C(x) \leq 1$ であるから，区間縮小法により従う．
&&&

&&&lem
(a) $C$ は $0$ において連続である．
(b) $S$ は $0$ において連続である．
&&&

&&&prf
(a) 補題 17 と補題 15 (a) より，従う．実際，

$\forall \epsilon > 0.\ \exists n_0.\ n > n_0 \Rightarrow \left|C\left(\dfrac{p}{2^n}\right)-1\right| < \varepsilon$

が補題 17 より成り立ち，$C$ の単調性から，上記条件下で $n_0$ に対し，$\forall x \in [0, p].\ |x| < \dfrac{p}{2^{n_0}} \Rightarrow |C(x)-1| < \varepsilon$ が成立するため，連続である．

(b) 補題 18 (a) と補題 3 (a) より，従う．実際，$C$ と連続関数 $x \mapsto x^2$ の合成は連続であり，定数関数 $x \mapsto 1$ との差 $x \mapsto 1-(C(x))^2 = (S(x))^2$ も連続である．$x \mapsto \sqrt{x}$ も連続であるから，これらの合成も連続であり，示される．
&&&

&&&lem
$S,\ C$ は連続である．
&&&

&&&prf
補題 18, 補題 6 (a) 補題 12 (a) より，$y = \Delta x$ として，

$\displaystyle\lim_{\Delta x \to 0} S(x+\Delta x) = \displaystyle\lim_{\Delta x \to 0} (S(x)C(\Delta x)+C(x)S(\Delta x))\\=S(x) \displaystyle\lim_{\Delta x \to 0} C(\Delta x)+C(x) \displaystyle\lim_{\Delta x \to 0} S(\Delta x) = S(x)C(0)+C(x)S(0) = S(x),$

$\displaystyle\lim_{\Delta x \to 0} C(x+\Delta x) = \displaystyle\lim_{\Delta x \to 0} (C(x)C(\Delta x)-S(x)S(\Delta x))\\=C(x) \displaystyle\lim_{\Delta x \to 0} C(\Delta x)-S(x) \displaystyle\lim_{\Delta x \to 0} S(\Delta x) = C(x)C(0)-S(x)S(0) = C(x).$

ここで，定数倍の極限値，和の極限値についての事実を用いた．
&&&

&&&lem
$S,\ C$ は $[0, p]$ 上で唯一に決まる．
&&&

&&&prf
$C(x)$ の値がわかっていれば，補題 12 (a) により帰納的に $C(kx)$, 補題 12 (c) より帰納的に $C\left(\dfrac{x}{2^n}\right)$ を得ることができる ($k,\ n$ は任意の正整数)．定義 1 1. より $C(p)=0$  であるから，$C(x),\ x = \dfrac{kp}{2^n},\ x \in [0, p]$ の値がわかっている．このような $x$ が $[0, p]$ の中に稠密に分布していることを示す．

$y \in [0,p]$ を取る．$a_0 = 0, b_0 = p$ とし，$c_0 = \frac{a+b}{2}$ に対し，$y \leq c_0$ ならば $a_1 = 0, b_1 = c_0$ そうでないならば $a_1 = c_0, b_1 = b_0$ とする．これを繰り返し，区間 $I_n = [a_n, b_n]$ の列を作ると，$y \in [a_n, b_n]$ は常に保たれ，$I_n \subseteq I_{n-1}\ (n \geq 1)$ であり，その幅は $b_n-a_n = \frac{1}{2}(b_{n-1}-a_{n-1}) = \frac{1}{2^n}(a_0-b_0)$ であるから，区間縮小法により，実数がただ一つ定まり，これが $y$ と一致する．すなわち，$\displaystyle\lim_{n \to \infty} a_n = \lim_{n \to \infty} b_n = y$ であり，$a_n, b_n$ は上記の $x$ の形をしている (これは帰納的に容易に示される) から，稠密性が示された．

よって，$C$ の連続性と稠密性から，一意に定まる．補題 3 (a) より，$S$ も定まる．
&&&

さて，これで上記の公理から出発して一意に連続関数 $C,\ S$ が定まることが示されました．お察しの通り，$p = \frac{\pi}{2}$ とした場合に $C$ が余弦関数，$S$ が正弦関数に対応しています．しかしながら，$\pi$ はどのように定義すれば良いのでしょうか？

以降では，$p = 1$ とし，定義域を $[0,1]$ に制限して，関数 $F$ を $F(x) = \dfrac{S(x)}{x},\ 0 < x \leq 1$ とします．これは連続関数 $S(x)$ と $x \mapsto \frac{1}{x}$ の積より明らかに連続関数です．

&&&thm
$F(x)$ は $(0, 1]$ 上の単調減少関数である．
&&&

先に以下の補題を示します．

&&&lem
任意の $x$ と正整数 $n$ であって，$0 < x < nx \leq 1$ を満たすものに対し，実数列 $F(x),\ F(2x),\ \ldots,\ F(nx)$ は単調減少である．
&&&

&&&prf
補題 6 (b), 補題 5 (d), 補題 1, 補題 15 (a), 補題 19 より，
$F(2x) = \dfrac{S(2x)}{2x} = \dfrac{2S(x)C(x)}{2x} = (F(x))C(x) < F(x).$
次に $F(kx) < F((k-1)x)$ を仮定し，$F((k+1)x) < F(kx)$ を示す．前提を整理すると，補題 13 より，

$F(kx) < F((k-1)x),\\\dfrac{S(kx)}{kx} < \dfrac{S((k-1)x}{(k-1)x},\\(k-1)S(kx) < kS((k-1)x),\\kS(kx)-S(kx) < kS(kx)C(x)-kC(kx)S(x).$

補題 5 (d) と上記より，

$kS(kx)C(x)-S(kx) \leq kS(kx)-S(kx),\\<kS(kx)C(x)-kC(kx)S(x),\\\leq kS(kx)-kC(kx)S(x).$

よって，

$kS(kx)C(x)+kC(kx)S(x)<kS(kx)+S(kx),\\kS((k+1)x) < (k+1)S(kx),\\F((k+1)x) < F(kx).$
&&&

&&&prf
上記定理の証明．

$0 < x_0 < y \leq 1$ とする．$k$ を $2^{-k}x_0 < y-x_0$ となるものとして定める．$x_1 = x_0 + 2^{-k}x_0 < y$ とおくと，$x_0 = 2^k(2^{-k}x_0)$, $x_1 = (2^k+1)(2^{-k}x_0)$ である．よって，上の補題より $F(x_0) > F(x_1)$ である．$\varepsilon = F(x_0)-F(x_1) > 0$ とおく．$F$ は連続であるから，$\exists \delta > 0. y-\delta < t < y \Rightarrow |F(y)-F(t)| < \varepsilon$ が成立する．特に $y-\delta < x_1 < y \Rightarrow F(y)-F(x_1) \leq |F(y)-F(x_1)| < \varepsilon = F(x_0)-F(x_1)$ が成り立つある $\delta > 0$ を取ることができる．このとき，$F(y) < F(x_0)$ である．一方，$x_1 \leq y-\delta$ ならば，$2^{-(k+j)} x_0 < \delta$ となるように正整数 $j$ を取ることができる．すると，アルキメデス性より，ある正整数 $n$ が存在して，$y-\delta < x_1+n(2^{-(k+j)})x_0 < y$ が成り立つ．$x_2 = x_1+n(2^{-(k+j)})x_0$ とすると，$x_1 = (2^j+2^{(j+k)})(2^{-(j+k)}x_0)$ と $x_2 = (2^j+2^{(j+k)}+n)(2^{-(j+k)}x_0)$．そして再び上記補題より，$F(x_2) < F(x_1)$ であり，$F(y)-F(x_2) \leq |F(y)-F(x_2)| < \varepsilon = F(x_0)-F(x_1) < F(x_0)-F(x_2)$. ゆえに，$F(y) < F(x_0)$ である．
&&&

次に極限値の存在を示します．

&&&thm
$\displaystyle\lim_{x \to 0} F(x)$ は存在する．
&&&

これを示すための補題をさらに用意します．

&&&lem
$n$ を非負整数として，

$\dfrac{2}{1+C(2^{-n})} \leq \dfrac{2}{2-2^{-n}}$.
&&&

&&&prf
補題 16 より，$C(2^{-n}) \geq 1-2^{-n}$ ならば，$C(2^{-(n+1)}) \geq 1-2^{-(n+1)}$ である．$C(2^{-0}) = C(1) = 0 \geq 1-2^{-0}$ であるから，帰納的に $C(2^{-n}) \geq 1-2^{-n}$ が任意の非負整数 $n$ について示される．よって，上記は成り立つ．
&&&

&&&lem
実数列 $(F(2^{-i}))\ (i=1,2,\ldots)$ は極限値を持つ．
&&&

&&&prf
補題 3 (a) と補題 12 (c) より，

$F^2\left(\dfrac{x}{2}\right) = \dfrac{(S(\frac{x}{2}))^2}{(\frac{x}{2})^2} = \dfrac{4}{x^2} \cdot \dfrac{1-C(x)}{2} = \dfrac{4}{x^2} \cdot \dfrac{1-(C(x))^2}{1+C(x)} \cdot \dfrac{1}{2}\\=\dfrac{2}{1+C(x)} \cdot \left(\dfrac{S(x)}{x}\right)^2 = \dfrac{2}{1+C(x)} F(x)$

であるから，$F^2(2^{-1}) = \dfrac{2}{1+C(1)}F^2(1) = 2 \leq \dfrac{2^{1+1}}{2^{1-1}+1}$ である．

$F^2(2^{-k}) \leq \dfrac{2^{k+1}}{2^{k-1}+1}$ を仮定すると，

$F^2(2^{-(k+1)})=\dfrac{2}{1+C(2^{-k})}F^2(2^{-k})\\\leq \dfrac{2}{2-2^{-k}} \cdot \dfrac{2^{k+1}}{2^{k-1}+1}\\=\dfrac{2^{k+2}}{2^k+1+(1-2^{-1}-2^{-k})}.$

$k \geq 1$ のとき，分母のカッコ内は非負なので，仮定した不等式が任意の正整数 $k$ について成り立つ．これはいずれも 4 で上から抑えられるため，考えている数列は有界であり，上記定理より単調増加であるから，有界な単調数列の収束性により，極限値を持つ．
&&&

&&&prf
上記定理の証明．

上記補題と $F(x)$ が減少関数であることから，従う (同様の議論を補題 18 の証明で行った)．
&&&

以上より，この極限値から $\pi$ を定義でき，通常の三角関数も定めることができます．

&&&def
$\pi = 2\displaystyle\lim_{x \to 0} F(x)$.
&&&

&&&def
$\sin x = S\left(\dfrac{2x}{\pi}\right),\ \cos x = C\left(\dfrac{2x}{\pi}\right)$.
&&&

以下は簡単に示せます．

&&&thm
$\displaystyle\lim_{x \to 0} \dfrac{\sin x}{x} = 1$.
&&&

&&&prf
$1 = \left(\dfrac{2}{\pi}\right)\cdot\left(\dfrac{\pi}{2}\right) = \dfrac{2}{\pi}\displaystyle\lim_{x \to 0} \dfrac{S(x)}{x} = \dfrac{2}{\pi} \displaystyle\lim_{x \to 0} \dfrac{S(\frac{2x}{\pi})}{\frac{2x}{\pi}}=\displaystyle\lim_{x \to 0} \dfrac{S(\frac{2x}{\pi})}{x} = \displaystyle\lim_{x \to 0} \dfrac{\sin x}{x}$.
&&&

## 解析の基礎知識
論理・集合・写像・実数の順序や演算やそれらの整合性，また区間等の基礎概念は既知とします．以下，単に数という場合は実数を指します．実数について，以下の連続性を要請します：

&&&thm デデキント切断
実数を $A,\ B$ の 2 組に分けて，任意の $a \in A$ と $b \in B$ について $a < b$ が成り立つ時，このような組み分け $(A, B)$ を **(デデキントの) 切断** という．特に実数の切断は下組と上組の境界として，一つの数を定める． すなわち，切断 $(A, B)$ に対し，一つの数 $s$ が存在して，$s$ が $A$ の最大数であって $B$ に最小数がないか，$A$ に最大数がなく $s$ が $B$ の最小数となるかのいずれかが成立する．
&&&

ここから以下が導かれます．

&&&thm ワイエルシュトラスの定理
実数の集合 $S \subseteq \mathbb{R}$ が上方 (下方) に有界 (それぞれ $S$ に属する全ての数がある一つの実数 $M$ よりも大 (小) でない時を指し， $M$ を一つの **上界 (下界)** と言う) ならば，$S$ の最小上界 (最大下界) が存在する．最小上界 を **上限**，最大下界を **下限** という．
&&&

&&&prf
$S$ が下方に有界として，下限の存在を示せばもう一方は同様であるから十分である．
$S$ の下界 $a$ に対し， $a$ より小さい数も下界であるから，下界全体の集合 $A$ と $B = \mathbb{R} \setminus A$ の組は切断である．なぜなら， 任意の $b \in B$ は下界でないので，任意の下界 $a \in A$ に対し $a < b$ が成立するからである．
この切断によって定まる数を $s$ とする．定理 1 より， $s$ は $A$ の最大数であるか，$B$ の最小数であるかのいずれかである．
$s \in B$ と仮定する．$s$ は下界でないので，ある $x$ に対し，$x < s$ が成立する．ここで $x < b < s$ なる実数 $b$ を取ると，$x < b$ より $b$ は下界でなく，$b \in B$ である．しかし，$b < s$ であるから，$s$ の最小性に矛盾する．
ゆえに，$s$ は $B$ の最小数ではなく，$A$ の最大数，すなわち下限である．
&&&

さらに数列の収束について述べていきます．

&&&def 数列の収束
実数列 $(a_n)$ が (実数 $\alpha$ に) **収束** する，または $\alpha$ が $a_n$ の **極限** であるとは，

$\forall \varepsilon > 0.\ \exists n_0 \in \mathbb{N}.\ n > n_0 \Rightarrow |a_n-\alpha| < \varepsilon$

が成立することを言い，

$\displaystyle\lim_{n \to \infty} a_n = \alpha$

と表記する．
&&&

&&&prop 極限の一意性
実数列 $(a_n)$ が極限値を持つならば，一意である．
&&&

&&&prf
$\alpha \neq \alpha'$ とし，$(a_n)$ が $\alpha, \alpha'$ に収束すると仮定すると，$|\alpha-\alpha'| \leq |a_n-\alpha|+|a_n-\alpha'|$ であり，十分大きな $n$ を取ればこれは任意の $\varepsilon > 0$ で上から抑えられるため，矛盾する．
&&&

&&&thm 収束列の有界性
$\displaystyle\lim_{n \to \infty} a_n = \alpha$ ならば，$\forall n \in \mathbb{N}. |a_n| < M$ なる定数 $M$ があり，$|\alpha| \leq M$ である．
&&&

&&&prf
任意の $\varepsilon > 0$ を取ると，$(a_n)$ の収束性から，

$n > p \Rightarrow \alpha-\varepsilon < a_n < \alpha+\varepsilon$

なる自然数 $p$ がある．そこで，$|a_1|, |a_2|, \ldots, |a_p|, |\alpha-\varepsilon|, |\alpha+\varepsilon|$ の $p+2$ 個の数のどれよりも大きい数を $M$ とすれば，$\forall n \in \mathbb{N}. |a_n| < M$ が成立する．

また，$|\alpha| > M$ と仮定すれば，$|\alpha| > M' > M$ なる $M'$ があり，$|\alpha-a_n| > M'-M > 0$ となり，矛盾するので，示された．
&&&

&&&thm 和・差・積・商の極限値
実数列 $(a_n),\ (b_n)$ が収束するとき，

1. $\displaystyle\lim_{n \to \infty} (a_n + b_n) = \lim_{n \to \infty} a_n + \lim_{n \to \infty} b_n$,
2. $\displaystyle\lim_{n \to \infty} (a_n - b_n) = \lim_{n \to \infty} a_n - \lim_{n \to \infty} b_n$,
3. $\displaystyle\lim_{n \to \infty} (a_nb_n) = \left(\lim_{n \to \infty} a_n\right)\left(\lim_{n \to \infty} b_n\right)$,
4. $\displaystyle\lim_{n \to \infty} \left(\dfrac{a_n}{b_n}\right) = \dfrac{\displaystyle\lim_{n \to \infty} a_n}{\displaystyle\lim_{n \to \infty} b_n}$.

ただし，4. では $b_n \neq 0$, $\displaystyle\lim_{n \to \infty}b_n \neq 0$ とする．
&&&

&&&prf
いわゆる絶対値の三角不等式から，1., 2. は明らかであろう．
そして 3. については，

$\alpha\beta-a_nb_n = (\alpha-a_n)\beta + a_n(\beta-b_n)$

であり，収束列の有界性より，$|\beta| < M, |a_n| < M$ とすれば，

$|\alpha\beta-a_nb_n| \leq M(|\alpha-a_n|+|\beta-b_n|)$.

$n$ を十分大きくすれば，右辺は任意の $\varepsilon$ で抑えられるため，示される．

さらに 4. については，

$\displaystyle\lim_{n \to \infty} \dfrac{1}{b_n} = \dfrac{1}{\beta}$

を示せば，3. と合わせて示せるので十分である．

仮定により，$|\beta| > 0$ であり，ある番号以上は $|b_n| > \dfrac{1}{2}|\beta|$ であるから，

$\left|\dfrac{1}{\beta}-\dfrac{1}{b_n}\right| = \left|\dfrac{b_n-\beta}{\beta b_n}\right|\\\leq \dfrac{2|b_n-\beta|}{|\beta|^2}.$

$n$ を十分大きくすれば，右辺は任意の $\varepsilon > 0$ で上から抑えられるので示された． 
&&&

&&&thm 有界な単調数列の収束
実数列 $(a_n)$ が **有界** であるとは，集合 $\{|a_n|\ \vert\ n \in \mathbb{N}\}$ が有界であることを言う．実数列 $(a_n)$ が番号とともに増大するならば **単調に増大する** と言い，減少するならば **単調に減少する** と言う． 単調増加あるいは単調減少であることを単に **単調** であると言う．有界な単調数列 $(a_n)$ は収束する．
&&&

&&&prf
単調増加の場合に示せば十分であろう．
有界な単調増加数列には全ての $n$ に対して $a_n < M$ となる定数 $M$ が存在する．その上限はワイエルシュトラスの定理により存在するので，それを $\alpha$ とする．すると $\alpha$ が $(a_n)$ の極限である．実際，$\alpha' < \alpha$ とすれば，上限の定義に従って $\alpha' < a_p \leq \alpha$ なる $a_p$ があるが，数列は単調増加であるため，$n > p$ のとき $\alpha' < a_n \leq \alpha$．よって，$|\alpha-a_n| < \alpha-\alpha'$ であり，$\alpha' < \alpha$ は任意であるから $\displaystyle\lim_{n \to \infty} a_n = \alpha$ である．
&&&

さらに以下が成り立ちます．

&&&thm 区間縮小法
閉区間 $I_n = [a_n, b_n]\ (n=1,2,\ldots)$ において，以下の 2 条件を満たすものとする：

1. 各区間 $I_n\ (n \geq 2)$ に対し，$I_n \subseteq I_{n-1}$,
2. $\displaystyle\lim_{n \to \infty} (b_n-a_n) = 0$.

このとき，各区間に属する実数がただ一つ存在する．
&&&

&&&prf
仮定 1. より， $a_1 \leq a_2 \leq \cdots \leq a_n \leq \cdots \leq b_n \leq \cdots \leq b_2 \leq b_1$ なので，数列 $(a_n), (b_n)$ は有界単調数列である．従って，上で示したことより極限値 $\alpha, \beta$ が存在する：
$\displaystyle\lim_{n \to \infty} a_n = \alpha,\ \displaystyle\lim_{n \to \infty} b_n = \beta$.
任意の $n, m$ に対し $a_n < b_m$ だから $\alpha \leq b_m$，よって $\alpha \leq \beta$．
仮定 2. により，任意の $\varepsilon > 0$ に対し，$b_n - a_n < \varepsilon$ なる $n$ が存在する． $a_n \leq \alpha \leq \beta \leq b_n$ より，$0 \leq \beta-\alpha < \varepsilon$．$\varepsilon$ は任意なので，$\alpha=\beta$．
&&&

さて，

i. デデキント切断
ii. ワイエルシュトラスの定理
iii. 有界な単調数列の収束
iv. 区間縮小法

のうち， i $\Rightarrow$ ii, ii $\Rightarrow$ iii, iii $\Rightarrow$ iv を示してきたわけですが，iv $\Rightarrow$ i も示すことができ，従って上の 4 つは互いに同値であることが以下に示されます．

&&&thm
上記 4 つ i 〜 iv は互いに同値である．
&&&

&&&prf
iv $\Rightarrow$ i を示す．
$(A, B)$ を切断とする．$A,\ B$ から 一つずつ $a, b$ を取り出して，$I_0 = [a,b]$ とする．さて，$\frac{a+b}{2}$ は $A$ または $B$ の一方に属するが，それぞれの場合について
$a_1 = \frac{a+b}{2}, b_1 = b$
または
$a_1 = a, b_1 = \frac{a+b}{2}$
と置けば $I_1 = [a_1, b_1]$ の左端は $A$ に属し，右端は $B$ に属し，その幅は $b_1-a_1 = \frac{1}{2}(b-a)$ である．
同様にして，区間の列 $I_0 \supseteq I_1 \supseteq I_2 \supseteq \cdots \supseteq I_n \supseteq \cdots$ であり，$I_n = [a_n, b_n],\ b_n-a_n = \frac{1}{2^n}(b-a)$ であるものを得るが，これは区間縮小法の仮定を満たすので，ある実数 $s$ が定まる．これは $A$ または $B$ のいずれかに属さなければならない．$s \in A$ とすると，$s< s'$ なる $s'$ に対し，$\displaystyle\lim_{n \to \infty} b_n = s$ であるから，$s < b_n < s'$ なる $b_n$ が存在するので，$s'$ は $B$ に属する．従って $s$ は $A$ の最大数である．このとき $B$ に最小数 $s'$ があったとすると，$s < b_n < s'$ なる $b_n$ が存在し，$b_n$ が $B$ に属するから，最小性に矛盾するので，$B$ に最小数はない．

$s \in B$ の場合も同様だから，i が示される．
&&&

ここから，以下のアルキメデス性が成り立ちます．

&&&thm アルキメデス性
$\forall \varepsilon > 0.\ \forall a > 0.\ \exists n \in \mathbb{N}.\ n\varepsilon > a$.
&&&

&&&prf
否定を取り，$\exists \varepsilon > 0.\ \exists a > 0.\ \forall n \in \mathbb{N}.\ n \leq \dfrac{a}{\varepsilon}$ が成り立つとする．ゆえに，全ての自然数の集合が上に有界であるから，ワイエルシュトラスの定理により上限 $s$ が存在する．上限の定義により $s-1 < m \leq s$ を満たす自然数 $m$ があるから，$s < m+1$．しかし，$m+1$ も自然数であるから，これは $s$ が上限であることに矛盾する．したがって示された．
&&&

また，集積点と稠密性について定義します．

&&&def 集積点と稠密性
集合 $S \subseteq \mathbb{R}$ に対し，$a \in \mathbb{R}$ が $S$ の **集積点** であるとは，$\forall \varepsilon > 0. \{|x-a| < \varepsilon \ \vert\ x \in \mathbb{R}\} \cap S \neq \emptyset$ が成立することを言う．また，$S$ の集積点全体の集合 $\overline{S}$ を $S$ の **閉包** と言う． $S$ を含む集合 $T$ を考え，$T \subseteq \overline{S}$ である場合に $S$ は $T$ の中に **稠密** に分布していると言う．
&&&

実数関数の収束，連続性について定義します．

&&&def 関数の収束
ある実数上の区間 $X$ 上で定義される関数 $f: \mathbb{R} \supseteq X \rightarrow \mathbb{R}$ が ($a \in \mathbb{R}$ において $\alpha \in \mathbb{R}$ に) **収束** する，または $\alpha$ が $f$ の $a$ における **極限** であるとは，

$\forall \varepsilon > 0.\ \exists \delta > 0.\ \forall x \in X.\ x \neq a , |x-a| < \delta \Rightarrow |f(x)-\alpha| < \varepsilon$

が成立することを言い，

$\displaystyle\lim_{x \to a} f(x) = \alpha$

と表記する．
&&&

&&&def 関数の単調性
ある実数上の区間 $X$ で定義される実数値関数 $f: \mathbb{R} \supseteq X \rightarrow \mathbb{R}$ が **単調増加関数** であるとは，$\forall x, y \in X. x < y \Rightarrow f(x) < f(y)$ が成立することを言う．同様に，

$\forall x, y \in X. x \leq y \Rightarrow f(x) \leq f(y),$ 

$\forall x, y \in X. x < y \Rightarrow f(x) > f(y),$ 

$\forall x, y \in X. x \leq y \Rightarrow f(x) \geq f(y)$ 

が成立することをそれぞれ，**単調非減少関数**, **単調減少関数**, **単調非増加関数** と言う．
&&&

&&&def 関数の連続性
ある実数上の区間 $X$ 上で定義される関数 $f: \mathbb{R} \supseteq X \rightarrow \mathbb{R}$ が $a \in X$ において **連続** であるとは，

$\forall \varepsilon > 0.\ \exists \delta > 0.\ \forall x \in X.\ |x-a| < \delta \Rightarrow |f(x)-f(a)| < \varepsilon$

が成立することを言う．特に $\displaystyle\lim_{x \to a} f(x) = f(a)$ である．

任意の $a \in X$ で連続であるとき，$f$ は単に連続であると言う．
&&&

&&&thm 和・差・積・商の連続性
ある実数上の区間 $X$ 上で定義される関数 $f, g: \mathbb{R} \supseteq X \rightarrow \mathbb{R}$ が $a \in X$ において連続であるとき，$f+g,\ f-g,\ fg,\ \dfrac{f}{g}$ も $a \in X$ において連続である．ただし，商については $g(a) \neq 0$ とする．
&&&

&&&prf
和・差・積・商の極限値から即座に従う．
&&&

いくつかの初等関数についての連続性を述べます．

&&&thm
定数関数 $x \mapsto c \in \mathbb{R}$ と線形関数 $x \mapsto x$ は連続である．

また，これらの和・差・積・商により作られる関数 (多項式関数や $x \mapsto \dfrac{1}{x}$ など) は連続である．

加えて，$x \mapsto \sqrt{x}$ も連続である．
&&&

&&&prf
定数関数が連続であることは自明であろう．線形関数の場合も，連続の定義における $\delta$ を $\varepsilon$ と等しくとれば成り立つことがわかる．

また，和・差・積・商の連続性により，2 番目の主張も従う．

$x \mapsto \sqrt{x}$ に関しては，$\sqrt{x}-\sqrt{a} = \dfrac{x-a}{\sqrt{x}+\sqrt{a}}$ より，示される．
&&&

連続関数同士の合成関数もやはり連続であることを示します．

&&&thm 合成関数の連続性
ある実数上の区間 $X$ 上で定義される関数 $f, g: \mathbb{R} \supseteq X \rightarrow \mathbb{R}$ が $a \in X$ において連続であるとき，$g \circ f: x \mapsto g(f(x))$ も $a \in X$ において連続である．
&&&

&&&prf
$f$ の連続性より，

$\forall \delta_2 > 0.\ \exists \delta_1 > 0.\ \forall x \in X.\ |x-a| < \delta_1 \Rightarrow |f(x)-f(a)| < \delta_2$

であり，$g$ の連続性より，

$\forall \varepsilon > 0.\ \exists \delta_2 > 0.\ \forall x \in X.\ |f(x)-f(a)| < \delta_2 \Rightarrow |g(f(x))-g(f(a))| < \varepsilon$

よって，

$\forall \varepsilon > 0.\ \exists \delta_1 > 0.\ \forall x \in X.\ |x-a| < \delta_1 \Rightarrow |g(f(x))-g(f(a))| < \varepsilon$

が成立し，連続性が示される．
&&&

また，稠密性と連続な関数の一致について示します．

&&&thm 稠密性と連続関数の一致
ある実数上の区間 $X$ 上で定義される連続関数を $f, g: X \rightarrow \mathbb{R}$ とする．$E \subseteq X$ を $X$ の中に稠密に分布する部分集合とし，$\forall x \in E. f(x)=g(x)$ が成り立つものとする．このとき，$\forall x \in X. f(x)=g(x)$ が成立する．
&&&

&&&prf
$X = E$ の場合は自明．
$X \neq E$ のとき，任意の $y \in X \setminus E$ を取る．このとき，$f, g$ の連続性から，

$\forall \varepsilon > 0.\ \exists \delta_1 > 0.\ \forall x \in X.\ |x-y| < \delta_1 \Rightarrow |f(x)-f(y)| < \dfrac{\varepsilon}{2}$,

$\forall \varepsilon > 0.\ \exists \delta_2 > 0.\ \forall x \in X.\ |x-y| < \delta_2 \Rightarrow |g(x)-g(y)| < \dfrac{\varepsilon}{2}$

が成り立つ．同一の $\varepsilon > 0$ に対応する $\delta_i\ (i=1,2)$ に対し，$\delta=\min\{\delta_1, \delta_2\}$ とすると，

$\forall \varepsilon > 0.\ \exists \delta > 0.\ \forall x \in X.\ |x-y| < \delta \Rightarrow |f(x)-f(y)| < \dfrac{\varepsilon}{2} \land |g(x)-g(y)| < \dfrac{\varepsilon}{2}$

である．この条件下で，$E$ の稠密性から，$E \cap \{x\ \vert\ |x-y| < \delta\} \neq \emptyset$ であり，ここから任意の元 $z$ をとってくると，$f(z)=g(z)$ であるから，

$|f(y)-g(y)| \leq |f(z)-f(y)| + |f(z)-g(y)| = |f(z)-f(y)| + |g(z)-g(y)| \\< \dfrac{\varepsilon}{2} + \dfrac{\varepsilon}{2} = \varepsilon$

が任意の $\varepsilon > 0$ について成り立つので，$f(y) = g(y)$ である．
&&&

## 参考文献
高木貞治 「定本　解析概論」, 岩波書店, 2010
Robison, "A new approach to circular functions, π, and lim sin(x)/x", Math. Mag. 41.2 (March 1968), 66–70.