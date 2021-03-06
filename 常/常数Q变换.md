{{expand|time=2016-07-27T03:06:21+00:00}}
'''常数Q变换'''（{{lang-en|Constant Q transform}}）是[[数学|数学]]和[[信号处理|信号处理]]中的变换，将数据变换到频域内。它与[[傅里叶变换|傅里叶变换]]相关<ref name="b91">Judith C. Brown, [http://www.wellesley.edu/Physics/brown/pubs/cq1stPaper.pdf Calculation of a constant Q spectral transform], ''J. Acoust. Soc. Am.'', 89(1):425–434, 1991.</ref>，而且与[[莫萊小波|莫萊小波]]变换紧密相关<ref>[https://ccrma.stanford.edu/~jos/sasp/Continuous_Wavelet_Transform.html Continuous Wavelet Transform] "When the mother wavelet can be interpreted as a windowed sinusoid (such as the Morlet wavelet), the wavelet transform can be interpreted as a constant-Q Fourier transform. Before the theory of wavelets, constant-Q Fourier transforms (such as obtained from a classic third-octave filter bank) were not easy to invert, because the basis signals were not orthogonal."</ref>。

常数Q变换可以視為是許多對數分佈濾波器的組合，其中第''k''個濾波器其頻寬是上一個濾波器頻寬的某個倍數，也就是

<math>\begin{align}
\delta f_k &= 2^{ \frac {1}{n} } * \delta f_{k-1}
\\ &= \left ( {2^{ \frac {1}{n} }} \right )^{k} * \delta f_{\mathrm{min}}
\end{align}</math>

其中
:δ''f<sub>k</sub>''為第''k''個濾波器的頻寬
:''f''<sub>min</sub>為最低濾波器的中心頻率
:''n'' 為每個[[Octave_(電子學)|Octave]]的濾波器數

== 參考資料 ==
{{reflist}}

[[Category:調和分析|Category:調和分析]]
[[Category:积分变换|Category:积分变换]]