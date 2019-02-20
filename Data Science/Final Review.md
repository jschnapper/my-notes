# Final Review

## Linear model
$$ y = f_\theta(x) + \epsilon $$
$y$ is the output
$\epsilon$ is some random noise
$f_\theta(x)$ is the mechanism by which our data is generated. This will always depend on our model. 

In the linear case 
$$f_\theta(x) = \theta_1(x) + \theta_0$$

In a constant case where we just trying to find a constant value for our model
$$ f_\theta(x) = \theta $$

When modeling, we are trying to predict the values of theta, therefore, our actual mechanism is

$$ f_{\hat{\theta}}(x) = \hat{\theta}_1(x) + \hat{\theta}_0 $$

**When performing multiple linear regression,**
$$f_{\hat{\theta}}(x) = \hat{\theta} \cdot x$$
$$f_{\hat{\theta}}(x) = \theta_0 + \hat{\theta}_1 \cdot x_1 + \hat{\theta}_2 \cdot x_2 ... + \hat{\theta}_n \cdot x_n$$
In this scenario $\theta$ and $x$ are both vectors and this is a dot product. $\theta$ is a weight and $x_i$ is the vector of values in a row of a dataframe.

As a result of this, when finding the partial derivative of each $\theta$, it is actually just equal to the vector at that index. 

**Need to keep track of vectors and scalars, because certain functions may require transposing.**

## Expectation
$$\mathbb{E}[X] = \sum_{x \in \mathbb{X}} x \cdot \mathbb{P}(X = x)$$
Where $X$ is a random variable

**Expectation Properties**
$$\mathbb{E}[X + Y] = \mathbb{E}[X] + \mathbb{E}[Y]$$
$$\mathbb{E}[cX] = c\mathbb{E}[X]$$

$\mathbb{E}[XY] = \mathbb{E}[X]\mathbb{E}[Y]$ is only true of ***independent random variables***


## Variance 
$$Var(X) = \mathbb{E}[(X -\mathbb{E}[X])^2] = \mathbb{E}[X^2]- \mathbb{E}[X]^2$$ 

**Variance Properties**
$$Var(aX + b) = a^2 Var(X)$$
If $X$ and $Y$ are ***independent random variables***, then $Var(X + Y) = Var(X) + Var(Y)$



