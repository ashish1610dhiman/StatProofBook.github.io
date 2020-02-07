---
layout: proof
mathjax: true

author: "Joram Soch"
affiliation: "BCCN Berlin"
e_mail: "joram.soch@bccn-berlin.de"
date: 2020-01-13 22:17:00

title: "Relation of mutual information to joint and conditional entropy"
chapter: "General Theorems"
section: "Information theory"
topic: "Discrete mutual information"
theorem: "Relation to joint and conditional entropy"

dependencies:
  - theorem: "relation of mutual information to marginal and conditional entropy"
    shortcut: "dmi-mce"
  - theorem: "relation of mutual information to marginal and joint entropy"
    shortcut: "dmi-mje"

sources:
  - authors: "Wikipedia"
    year: 2020
    title: "Mutual information"
    in: "Wikipedia, the free encyclopedia"
    pages: "retrieved on 2020-01-13"
    url: "https://en.wikipedia.org/wiki/Mutual_information#Relation_to_conditional_and_joint_entropy"

proof_id: "P21"
shortcut: "dmi-jce"
username: "JoramSoch"
---


**Theorem:** Let $X$ and $Y$ be discrete random variables with the joint probability $p(x,y)$ for $x \in \mathcal{X}$ and $y \in \mathcal{Y}$. Then, the mutual information of $X$ and $Y$ can be expressed as

$$ \label{eq:dmi-jce}
\mathrm{I}(X,Y) = \mathrm{H}(X,Y) - \mathrm{H}(X|Y) - \mathrm{H}(Y|X)
$$

where $\mathrm{H}(X,Y)$ is the joint entropy of $X$ and $Y$ and $\mathrm{H}(X \mid Y)$ and $\mathrm{H}(Y \mid X)$ are the conditional entropies.


**Proof:** The existence of the joint probability function ensures that the mutual information is defined:

$$ \label{eq:MI}
\mathrm{I}(X,Y) = \sum_{x \in \mathcal{X}} \sum_{y \in \mathcal{Y}} p(x,y) \log \frac{p(x,y)}{p(x)\,p(y)} \; .
$$

The relation of mutual information to conditional entropy is:

$$ \label{eq:dmi-mce1}
\mathrm{I}(X,Y) = \mathrm{H}(X) - \mathrm{H}(X|Y)
$$

$$ \label{eq:dmi-mce2}
\mathrm{I}(X,Y) = \mathrm{H}(Y) - \mathrm{H}(Y|X)
$$

The relation of mutual information to joint entropy is:

$$ \label{eq:dmi-mje}
\mathrm{I}(X,Y) = \mathrm{H}(X) + \mathrm{H}(Y) - \mathrm{H}(X,Y) \; .
$$

It is true that

$$ \label{eq:MI-s1}
\mathrm{I}(X,Y) = \mathrm{I}(X,Y) + \mathrm{I}(X,Y) - \mathrm{I}(X,Y) \; .
$$

Plugging in \eqref{eq:dmi-mce1}, \eqref{eq:dmi-mce2} and \eqref{eq:dmi-mje} on the right-hand side, we have

$$ \label{eq:MI-s2}
\begin{split}
\mathrm{I}(X,Y) &= \mathrm{H}(X) - \mathrm{H}(X|Y) + \mathrm{H}(Y) - \mathrm{H}(Y|X) - \mathrm{H}(X) - \mathrm{H}(Y) + \mathrm{H}(X,Y) \\
&= \mathrm{H}(X,Y) - \mathrm{H}(X|Y) - \mathrm{H}(Y|X)
\end{split}
$$

which proves the identity given above.