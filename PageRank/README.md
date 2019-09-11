# PageRank
## Iteration method
$$P_{n+1}=\alpha SP_n+\frac{1-\alpha}{N}e^T$$
$$A=\alpha S+\frac{1-\alpha}{N}ee^T$$
$$P_{n+1}=AP_n$$
Iteration ends when:
$$|P_{n+1}-P_n|< \epsilon$$
## Algebra method
$$P=\alpha SP+\frac{1-\alpha}{N}e^T$$
$$\Rightarrow(E-\alpha S)=\frac{1-\alpha}{N}e^T$$
$$\Rightarrow P=(E-\alpha S)^{-1}\frac{1-\alpha}{N}e^T$$