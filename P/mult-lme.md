---
layout: proof
mathjax: true

author: "Joram Soch"
affiliation: "BCCN Berlin"
e_mail: "joram.soch@bccn-berlin.de"
date: 2020-03-11 15:17:00

title: "Log model evidence for multinomial observations"
chapter: "Statistical Models"
section: "Categorical data"
topic: "Multinomial observations"
theorem: "Log model evidence"

sources:

proof_id: "P81"
shortcut: "mult-lme"
username: "JoramSoch"
---


**Theorem:** Let $y = [y_1, \ldots, y_k]$ be the number of observations in $k$ categories resulting from $n$ independent trials with unknown category probabilities $p = [p_1, \ldots, p_k]$, such that $y$ follows a [multinomial distribution](/D/mult):

$$ \label{eq:Mult}
y \sim \mathrm{Mult}(n,p) \; .
$$

Moreover, assume a [Dirichlet prior distribution](/P/mult-prior) over the model parameter $p$:

$$ \label{eq:Mult-prior}
\mathrm{p}(p) = \mathrm{Dir}(p; \alpha_0) \; .
$$

Then, the [posterior distribution](/D/post) is also a [Dirichlet distribution](/D/dir)

$$ \label{eq:Mult-LME}
\begin{split}
\log \mathrm{p}(y|m) = \log {n \choose {y_1, \ldots, y_k}} &+ \log \Gamma \left( \sum_{j=1}^{k} \alpha_{0j} \right) - \log \Gamma \left( \sum_{j=1}^{k} \alpha_{nj} \right) \\
&+ \sum_{j=1}^k \log \Gamma(\alpha_{nj}) - \sum_{j=1}^k \log \Gamma(\alpha_{0j}) \; .
\end{split}
$$

and the [posterior hyperparameters](/D/post-hyp) are given by

$$ \label{eq:Mult-post-par}
\alpha_{nj} = \alpha_{0j} + y_j, \; j = 1,\ldots,k \; .
$$


**Proof:** With the [probability mass function of the multinomial distribution](/P/mult-pmf), the [likelihood function](/D/lf) implied by \eqref{eq:Mult} is given by

$$ \label{eq:Mult-LF}
\mathrm{p}(y|p) = {n \choose {y_1, \ldots, y_k}} \prod_{j=1}^{k} {p_j}^{y_j} \; .
$$

Combining the likelihood function \eqref{eq:Mult-LF} with the prior distribution \eqref{eq:Mult-prior}, the [joint likelihood](/D/jl) of the model is given by

$$ \label{eq:Mult-JL}
\begin{split}
\mathrm{p}(y,p) &= \mathrm{p}(y|p) \, \mathrm{p}(p) \\
&= {n \choose {y_1, \ldots, y_k}} \prod_{j=1}^{k} {p_j}^{y_j} \cdot \frac{\Gamma \left( \sum_{j=1}^{k} \alpha_{0j} \right)}{\prod_{j=1}^k \Gamma(\alpha_{0j})} \prod_{j=1}^{k} {p_j}^{\alpha_{0j}-1} \\
&= {n \choose {y_1, \ldots, y_k}} \frac{\Gamma \left( \sum_{j=1}^{k} \alpha_{0j} \right)}{\prod_{j=1}^k \Gamma(\alpha_{0j})} \prod_{j=1}^{k} {p_j}^{\alpha_{0j}+y_j-1} \; .
\end{split}
$$

Note that the model evidence is the marginal density of the joint likelihood:

$$ \label{eq:Mult-ME-s1}
\mathrm{p}(y) = \int \mathrm{p}(y,p) \, \mathrm{d}p \; .
$$

Setting $\alpha_{nj} = \alpha_{0j} + y_j$, the joint likelihood can also be written as

$$ \label{eq:Mult-JL-s2}
\mathrm{p}(y,p) = {n \choose {y_1, \ldots, y_k}} \frac{\Gamma \left( \sum_{j=1}^{k} \alpha_{0j} \right)}{\prod_{j=1}^k \Gamma(\alpha_{0j})} \, \frac{\prod_{j=1}^k \Gamma(\alpha_{nj})} {\Gamma \left( \sum_{j=1}^{k} \alpha_{nj} \right)} \, \frac{\Gamma \left( \sum_{j=1}^{k} \alpha_{nj} \right)}{\prod_{j=1}^k \Gamma(\alpha_{nj})} \prod_{j=1}^{k} {p_j}^{\alpha_{nj}-1} \; .
$$

Using the [probability density function of the Dirichlet distribution](/P/dir-pdf), $p$ can now be integrated out easily

$$ \label{eq:Mult-ME-qed}
\begin{split}
\mathrm{p}(y) &= \int {n \choose {y_1, \ldots, y_k}} \frac{\Gamma \left( \sum_{j=1}^{k} \alpha_{0j} \right)}{\prod_{j=1}^k \Gamma(\alpha_{0j})} \, \frac{\prod_{j=1}^k \Gamma(\alpha_{nj})}{\Gamma \left( \sum_{j=1}^{k} \alpha_{nj} \right)} \, \frac{\Gamma \left( \sum_{j=1}^{k} \alpha_{nj} \right)}{\prod_{j=1}^k \Gamma(\alpha_{nj})} \prod_{j=1}^{k} {p_j}^{\alpha_{nj}-1} \, \mathrm{d}p \\
&= {n \choose {y_1, \ldots, y_k}} \frac{\Gamma \left( \sum_{j=1}^{k} \alpha_{0j} \right)}{\prod_{j=1}^k \Gamma(\alpha_{0j})} \, \frac{\prod_{j=1}^k \Gamma(\alpha_{nj})}{\Gamma \left( \sum_{j=1}^{k} \alpha_{nj} \right)} \int \mathrm{Dir}(p; \alpha_n) \, \mathrm{d}p \\
&= {n \choose {y_1, \ldots, y_k}} \frac{\Gamma \left( \sum_{j=1}^{k} \alpha_{0j} \right)}{\Gamma \left( \sum_{j=1}^{k} \alpha_{nj} \right)} \, \frac{\prod_{j=1}^k \Gamma(\alpha_{nj})}{\prod_{j=1}^k \Gamma(\alpha_{0j})} \; ,
\end{split}
$$

such that the log model evidence is shown to be

$$ \label{eq:Mult-LME-qed}
\begin{split}
\log \mathrm{p}(y|m) = \log {n \choose {y_1, \ldots, y_k}} &+ \log \Gamma \left( \sum_{j=1}^{k} \alpha_{0j} \right) - \log \Gamma \left( \sum_{j=1}^{k} \alpha_{nj} \right) \\
&+ \sum_{j=1}^k \log \Gamma(\alpha_{nj}) - \sum_{j=1}^k \log \Gamma(\alpha_{0j}) \; .
\end{split}
$$