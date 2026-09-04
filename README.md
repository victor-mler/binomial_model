# Binomial Option Pricing (Cox-Ross-Rubinstein)

Victor Miller · [GitHub](https://github.com/victor-mler) · [LinkedIn](https://www.linkedin.com/in/miller-victor)

An implementation of the Cox-Ross-Rubinstein binomial model for European and American options, put-call parity and the hedging delta.

## Table of Contents

- [How the model works](#how-the-model-works)
- [What is inside](#what-is-inside)
- [Getting started](#getting-started)
- [Repository structure](#repository-structure)
- [License](#license)


## How the model works

At each step the stock moves up by a factor $u = e^{\sigma \sqrt{\Delta t}}$ or down by $d = \frac{1}{u}$, with $\Delta t = \frac{t}{n}$. The risk-neutral probability of an up move,

$$p = \frac{e^{r \Delta t} - d}{u - d}$$

is chosen so that the stock earns the risk-free rate on average. The option is priced backwards from its payoff at maturity, discounting each node at the risk-free rate. As $n$ grows, the tree price converges to the Black-Scholes price.

## What is inside

The notebook is self-contained: no API keys, no market data, nothing downloaded. It has three parts:

- the model: the CRR tree in one NumPy function, with the hedge delta read from the root
- a first run at 5,000 steps: price and delta
- put-call parity: call minus put compared to $S_0 - Ke^{-rt}$

## Getting started

1. Install the dependency:

   ```
   pip install -r requirements.txt
   ```

2. Open `binomial_model.ipynb` and run all cells.

## Repository structure

```
binomial_model/
├── binomial_model.ipynb   # the model and its validation
├── README.md
├── requirements.txt
├── LICENSE.txt
└── .gitignore
```

## License

[MIT](LICENSE.txt)