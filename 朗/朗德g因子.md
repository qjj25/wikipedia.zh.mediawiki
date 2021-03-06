{{NoteTA|G1=物理學}}
{{DISPLAYTITLE|朗德''g''因子}}
在[[物理学|物理学]]和[[化学|化学]]中，'''朗德<math>g</math>因子'''是[[阿尔佛雷德·朗德|阿尔佛雷德·朗德]]试图解释反常[[塞曼效应|塞曼效应]]时，于1921年提出的一个[[无量纲|无量纲]]物理量<ref>{{cite journal|title=Über den anomalen Zeemaneffekt (Teil I)|journal=Zeitschrift für Physik|doi=10.1007/bf01335014|url=https://link.springer.com/article/10.1007/BF01335014|date=1921-07-01|volume=5|issue=4|language=de|pages=231–241|issn=0044-3328|accessdate=2018-04-02|author=A. Landé}}</ref><ref>{{cite journal|title=Über den anomalen Zeemaneflekt (II. Teil)|journal=Zeitschrift für Physik|doi=10.1007/bf01332807|url=https://link.springer.com/article/10.1007/BF01332807|date=1921-12-01|volume=7|issue=1|language=de|pages=398–405|issn=0044-3328|accessdate=2018-04-02|author=A. Landé}}</ref><ref>{{cite journal|title=Zur Theorie der anomalen Zeeman- und magneto-mechanischen Effekte|journal=Zeitschrift für Physik|doi=10.1007/bf01328427|url=https://link.springer.com/article/10.1007/BF01328427|date=1922-12-01|volume=11|issue=1|language=de|pages=353–363|issn=0044-3328|accessdate=2018-04-02|author=A. Landé}}</ref><ref>{{cite journal|title=Termstruktur und Zeemaneffekt der Multipletts|journal=Zeitschrift für Physik|doi=10.1007/bf01330473|url=https://link.springer.com/article/10.1007/BF01330473|date=1923-12-01|volume=15|issue=1-2|language=de|pages=189–205|issn=0044-3328|accessdate=2018-04-02|author=A. Landé}}</ref>，反映了塞曼效应中[[磁矩|磁矩]]与[[角动量|角动量]]之间的联系。其定义后来被推广到其它领域，在[[粒子物理学|粒子物理学]]中常常被简称为<math>g</math>因子。

== 塞曼效应 ==
塞曼效应中的朗德<math>g</math>因子由下式给出<ref>''Quantum Chemistry: Fifth Edition'', Ira N. Levine, 2000</ref>
:<math>g_J=1+\frac{J(J+1)-L(L+1)+S(S+1)}{2J(J+1)}</math>

式中<math>L,S,J</math>分别是[[原子|原子]]能态（光谱支项）的[[角量子数|角量子数]]、[[自旋量子数|自旋量子数]]和内[[量子数|量子数]]。

=== 导引 ===
朗德假定<ref name="quantatom">{{cite book|title=Quantum Theory of Atomic Structure|author={{link-en|约翰·斯莱特|John C. Slater|John C. Slater}}|year=1960|chapter=10|isbn=9780070580404}}</ref>，当两个角动量<math>\mathbf{L}\hbar</math>与<math>\mathbf{S}\hbar</math>[[角动量耦合|耦合]]时，它们的相互作用能由下式给出：
:<math>E_{\text{interaction}}=\Gamma(\mathbf{L}\cdot\mathbf{S}),\quad \Gamma\,\text{ constant}</math>

令
:<math>\mathbf{J}\hbar=\mathbf{L}\hbar+\mathbf{S}\hbar</math>
为耦合后的总角动量，则可以证明<ref name="quantatom" />，在上述形式的相互作用能下，<math>\mathbf{L}\hbar</math>与<math>\mathbf{S}\hbar</math>将绕向量<math>\mathbf{J}\hbar</math>[[进动|进动]]。

在外加磁场的作用下，带电粒子的角动量会绕外加磁场的方向进动。在这种情况下，是<math>\mathbf{J}\hbar</math>进行进动。朗德采用了一种简化处理的方法，即认为外磁场中的原子的能量仅仅与向量<math>\mathbf{L}\hbar</math>与<math>\mathbf{S}\hbar</math>的长时间[[平均值|平均值]]有关，而后者恰好就是它们在<math>\mathbf{J}\hbar</math>方向上的[[投影|投影]]，即<ref name="quantatom" />
:<math>(\mathbf{L})_{\text{av}}=\frac{\mathbf{J}(\mathbf{L}\cdot\mathbf{J})}{J^2},\quad (\mathbf{S})_{\text{av}}=\frac{\mathbf{J}(\mathbf{S}\cdot\mathbf{J})}{J^2}</math>

随后，朗德进一步假定，角动量<math>\mathbf{L}\hbar</math>贡献的{{link-en|磁能|magnetic energy}}由经典的公式给出，并假定<math>\mathbf{J}\hbar</math>是量子化的，其沿着磁场方向的分量由磁量子数<math>M</math>确定，即
:<math>E_{\text{magnetic},L}=-\boldsymbol{\mu}\cdot\mathbf{B}=\left(\frac {e}{2m}(\mathbf{L})_{\text{av}}\hbar\right)\cdot\mathbf{B}
=(\mathbf{L})_{\text{av}}\cdot\mathbf{B}\mu_B=\frac{M(\mathbf{L}\cdot\mathbf{J})}{J^2}\mu_BB</math>

式中<math>\boldsymbol{\mu}</math>是[[磁矩|磁矩]]，而<math>\mu_B</math>為[[波耳磁子|波耳磁子]]。类似地，朗德写出了角动量<math>\mathbf{S}\hbar</math>带来的能量贡献，但他发现为了与实验结果相一致，需要加上额外的因子2。当时朗德并不清楚为什么<ref name="quantatom" />，现在我们知道这就是电子的自旋<math>g</math>因子。即：
:<math>E_{\text{magnetic},S}=\frac{M(\mathbf{S}\cdot\mathbf{J})}{J^2}2\mu_BB</math>

将上面结果加起来，朗德得到下列的表达式，并引入符号<math>g</math><ref name="quantatom" />，这就是朗德<math>g</math>因子的最早来源：
:<math>E_{\text{magnetic}}=\frac{M[(\mathbf{L}+2\mathbf{S})\cdot\mathbf{J}]}{J^2}\mu_BB=gM\mu_BB</math>

利用关系式<math>\mathbf{L}</math>+<math>2 \mathbf{S}</math>=<math>\mathbf{J}</math>+<math>\mathbf{S}</math>，朗德得到：
:<math>g=\frac{(\mathbf{L}+2\mathbf{S})\cdot\mathbf{J}}{J^2}=1+\frac{\mathbf{S}\cdot\mathbf{J}}{J^2}=1+\frac{J^2-L^2+S^2}{2J^2}</math>

但是，朗德发现，为了与实验结果相符，这一表达式需要修改为下式，当时朗德并不清楚原因<ref name="quantatom" />。现在来看，只要将上面的角动量矢量都作为[[算符|算符]]来处理，然后将对应的[[角动量算符|角动量平方算符]]用其[[本征值|本征值]]取代，得出这个结果是很自然的。
:<math>g=1+\frac{J(J+1)-L(L+1)+S(S+1)}{2J(J+1)}</math>

=== 推广 ===
从上面的导引可见，定义朗德<math>g</math>因子的式子是
:<math>E_{\text{magnetic}}=gM\mu_BB</math>

上式可以等价地表述为{{NoteTag|这里的<math>\mathbf{J}</math>相当于导引里的<math>\mathbf{J}\hbar</math>}}：
:<math>\boldsymbol{\mu}_J=g\frac{e}{2m}\mathbf{J}</math>

很自然的推广是将两边的<math>J</math>同时换成<math>L,S</math>等，并对不同的粒子将<math>m</math>换成对应粒子的质量。这就是现在广泛使用的朗德<math>g</math>因子。

== 粒子物理学 ==
粒子物理学中的<math>g</math>因子是自旋<math>g</math>因子，根据自旋角动量和自旋磁矩按照上面的形式定义。

=== 电子 ===
上面的导引已经给出了电子自旋<math>g</math>因子的定义。在实际使用中，它的符号有两种取法，用不同的符号表记：
:<math>g_{\rm e}\approx -2.002319, g_S=|g_{\rm e}|=-g_{\rm e}</math>

==== 歷史沿革 ====
歷史上，它的理論值有過變動：

* 在[[非相對論量子力學|非相對論量子力學]]理論下考慮[[自旋-軌道作用|自旋-軌道作用]]時，等效地說，<math>g_s</math>為1。
** 若再額外考慮[[狹義相對論|狹義相對論]][[時間展長|時間展長]]效應下的[[湯瑪斯進動|湯瑪斯進動]]修正（1927年），<math>g_s</math>變為2，方合乎當代實驗觀測值。
* 在[[相對論量子力學|相對論量子力學]]，也就是指[[保羅·狄拉克|保羅·狄拉克]]所提出的理論（1928年），<math>g_s</math>恰恰為2；並不如前者採外加修正的方法，是具有一致性的理論可導出的自然結果。
* 在[[量子電動力學|量子電動力學]]（QED）中，因為電子與[[真空能量|真空能量]]的電磁漲落交互作用，可表為[[單環費因曼圖|單環費因曼圖]]，提出QED的[[朱利安·施温格|朱利安·施温格]]等人（1947年）所得的<math>g_s</math>理論值为<math>\left( 2 + \frac{\alpha}{2\pi} + O(\alpha^2) \right) \approx 2.002\ 319\ 304\ 402</math><ref>V. W. Hughes and T. Kinoshita "Anomalous ''g'' values of the electron and muon" ''Review of Modern Physics'' 71, 133（1999）</ref>；α目前被視為是自然常數之一，其值約為<math>\frac{1}{137.035\ 999\ 11(46)}</math>。

[[威利斯·蘭姆|威利斯·蘭姆]]等人實驗觀測到的[[蘭姆位移|蘭姆位移]]效應，所得<math>g_s</math>觀測值为<math>2.002\ 319\ 304\ 376\ 8(86)</math>，與理論相符精準度達小數點下第9位，展現出量子電動力學等現代物理理論所能達到的驚人精準預測程度。

=== 其它粒子 ===
一些粒子的朗德<math>g</math>因子列表如下：
{| class="wikitable centre"
|+ [[NIST|NIST]] 提供的朗德<math>g</math>因子的值<ref>{{cite web|url=http://physics.nist.gov/cgi-bin/cuu/Results?search_for=g+factor|title=CODATA Values of the Fundamental Constants}}</ref>
|-
!scope=col | [[粒子|粒子]]
!scope=col | 朗德<math>g</math>因子
!scope=col | [[不确定性|{{math]]
|-
! scope=row | [[电子|电子]]
| -2.002 319 304 361 53 || 0.000 000 000 000 53
|-
! scope=row | [[中子|中子]]
| -3.826 085 45       || 0.000 000 90
|-
! scope=row | [[质子|质子]]
| 5.585 694 713      || 0.000 000 046
|-
! scope=row |[[μ子|μ子]]
| -2.002 331 8418     || 0.000 000 0013
|}

== 注釋 ==
{{NoteFoot}}

== 參考文獻 ==
{{Reflist}}

== 参见 ==
* [[波耳磁子|波耳磁子]]
* [[湯瑪斯進動|湯瑪斯進動]]
* [[量子電動力學|量子電動力學]]
* [[電子自旋共振|電子自旋共振]]

[[Category:量子力学|D]]