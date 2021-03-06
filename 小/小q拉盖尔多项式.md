[[File:Little_q-Laguerre_polynomials.gif|thumb]]
'''小q拉盖尔多项式'''是一个以[[基本超几何函数|基本超几何函数]]定义的[[正交多项式|正交多项式]]

:<math>\displaystyle  p_n(x;a|q) = {}_2\phi_1(q^{-n},0;aq;q,qx) = \frac{1}{(a^{-1}q^{-n};q)_n}{}_2\phi_0(q^{-n},x^{-1};;q,x/a)  </math>
==极限关系==

;大q拉盖尔多项式→小q拉盖尔多项式
在大q拉盖尔多项式中，令<math>x \to  bqx</math>,并令<math>b \to \infty</math>即得小q拉盖尔多项式

<math>\lim_{b \to \infty}P_{n}(bqx;a,b;q)=p_{n}(x;a|q)</math>

[[仿射Q克拉夫楚克多项式|仿射Q克拉夫楚克多项式]]→ 小q拉盖尔多项式：

<math>\lim_{a \to 1}=K_{n}^{aff}(q^{x-N};p,N|q)=p_{n}(q^x;p,q)</math>
令小q拉盖尔多项式  <math>a=q^a</math>  <math>x=(1-q)*x</math>,然后令q→1
即得[[拉盖尔多项式|拉盖尔多项式]]

<math>\lim_{q \to 1}P_{a}(1-q)x;q^a|q)=\frac{L_{n}^{(a)}(x)}{L_{n}^{(a)}(0)}</math>

;验证 9阶小q拉盖尔多项式→拉盖尔多项式 

作上述代换，


<math>

P_{a}(1-q)x;q^a|q) =1+{\frac {qx}{1-{q}^{\alpha}q}}-{\frac {x}{{q}^{8} \left( 1-{q}^{\alpha}q \right) }}</math>
<math>+ \left( 1-{q}^{-9} \right)  \left( 1-{q}^{-8}
\right) {q}^{2} \left( 1-q \right) {x}^{2} \left( 1-{q}^{2} \right) ^
{-1} \left( 1-{q}^{\alpha}q \right) ^{-1} \left( 1-{q}^{\alpha}{q}^{2}
\right) ^{-1}  </math><math>
+ \left( 1-{q}^{-9} \right)  \left( 1-{q}^{-8} \right) 
\left( 1-{q}^{-7} \right) {q}^{3} \left( 1-q \right) ^{2}{x}^{3}
\left( 1-{q}^{2} \right) ^{-1} </math><math>\left( 1-{q}^{3} \right) ^{-1} \left( 
1-{q}^{\alpha}q \right) ^{-1} \left( 1-{q}^{\alpha}{q}^{2} \right) ^{-
1} \left( 1-{q}^{\alpha}{q}^{3} \right) ^{-1}+\cdots


</math>






求q→1极限得
[[File:LimqLaguerre.JPG|860px]]

令a=3,得
<math> (1-{\frac {9}{4}}x+{\frac {9}{5}}{x}^{2}-{\frac {7}{10}}{x}^{3}+{
\frac {3}{20}}{x}^{4}-{\frac {3}{160}}{x}^{5}+{\frac {1}{720}}{x}^{6}-
{\frac {1}{16800}}{x}^{7}+{\frac {1}{739200}}{x}^{8}-{\frac {1}{
79833600}}{x}^{9})

 </math>

另一方面

<math>\frac{L_{n}^{(3)}(x)}{L_{n}^{(3)}(0)}</math>
=<math> (1-{\frac {9}{4}}x+{\frac {9}{5}}{x}^{2}-{\frac {7}{10}}{x}^{3}+{
\frac {3}{20}}{x}^{4}-{\frac {3}{160}}{x}^{5}+{\frac {1}{720}}{x}^{6}-
{\frac {1}{16800}}{x}^{7}+{\frac {1}{739200}}{x}^{8}-{\frac {1}{
79833600}}{x}^{9})
     </math>

二者显然相等   QED

==图集==
{|
|[[File:LITTLE_Q-LAGUERRE_POLYNOMIALS_ABS_COMPLEX_3D_MAPLE_PLOT.gif|thumb]]
|[[File:LITTLE_Q-LAGUERRE_POLYNOMIALS_IM_COMPLEX_3D_MAPLE_PLOT.gif|thumb]]
|[[File:LITTLE_Q-LAGUERRE_POLYNOMIALS_RE_COMPLEX_3D_MAPLE_PLOT.gif|thumb]]
|}
{|
|[[File:LITTLE_Q-LAGUERRE_POLYNOMIALS_ABS_DENSITY_MAPLE_PLOT.gif|thumb]]
|[[File:LITTLE_Q-LAGUERRE_POLYNOMIALS_IM_DENSITY_MAPLE_PLOT.gif|thumb]]
|[[File:LITTLE_Q-LAGUERRE_POLYNOMIALS_RE_DENSITY_MAPLE_PLOT.gif|thumb]]
|}

==参考文献==

*{{Citation | last1=Chihara | first1=Theodore Seio | title=An introduction to orthogonal polynomials | url=http://books.google.com/books?id=IkCJSQAACAAJ | publisher=Gordon and Breach Science Publishers | location=New York | series=Mathematics and its Applications | isbn=978-0-677-04150-6 | mr=0481884 |id= Reprinted by Dover 2011, ISBN 978-0-486-47929-3 | year=1978 | volume=13}}
*{{Citation | last1=Gasper | first1=George | last2=Rahman | first2=Mizan | title=Basic hypergeometric series | publisher=[[Cambridge_University_Press|Cambridge University Press]] | edition=2nd | series=Encyclopedia of Mathematics and its Applications | isbn=978-0-521-83357-8 | doi=10.2277/0521833574 | mr=2128719 | year=2004 | volume=96}}
*{{Citation | last1=Koekoek | first1=Roelof | last2=Lesky | first2=Peter A. | last3=Swarttouw | first3=René F. | title=Hypergeometric orthogonal polynomials and their q-analogues | publisher=[[Springer-Verlag|Springer-Verlag]] | location=Berlin, New York | series=Springer Monographs in Mathematics | isbn=978-3-642-05013-8 | doi=10.1007/978-3-642-05014-5 | mr=2656096 | year=2010}}
*{{dlmf|id=18|title=|first=Tom H. |last=Koornwinder|first2=Roderick S. C.|last2= Wong|first3=Roelof |last3=Koekoek||first4=René F. |last4=Swarttouw}}
*{{Citation | last1=Van Assche | first1=Walter | last2=Koornwinder | first2=Tom H. | title=Asymptotic behaviour for Wall polynomials and the addition formula for little q-Legendre polynomials | doi=10.1137/0522019 | mr=MR1080161 | year=1991 | journal=SIAM Journal on Mathematical Analysis | issn=0036-1410 | volume=22 | issue=1 | pages=302–311}}
*{{Citation | last1=Wall | first1=H. S. | title=A continued fraction related to some partition formulas of Euler | jstor=2303599 | mr=0003641 | year=1941 | journal=[[American_Mathematical_Monthly|The American Mathematical Monthly]] | issn=0002-9890 | volume=48 | pages=102–108}}
{{q超几何函数}}
[[Category:正交多项式|Category:正交多项式]]