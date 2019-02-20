#### 3/15 | Bias Variance Tradeoff

Can still have a **linear model** in terms of the parameters $\Theta$ even though the function is a polynomial, i.e. $f_\Theta(x) = \Theta_0 + \Theta_1x + \Theta_2x^2 + ... + \Theta_nx^n$ because the model is linear combination of the paramaters

**Bias**: the expected deviation between the predicted value and the true value

**Variance**: two sources
* **Observation Variance**: the variability of the random noise in the process we are trying to model
* **Estimated Model Variance**: the variability in the predicted value across different training datasets

Overfitting is the result of specifying too much from a given model. The model that is generated is too much like this instance, and given new observations, won't reflect the additional observations. It may look good initially, but doesn't do well with new data points. 

Very simple model (reduced bias) but won't describe data well. Tradeoff between variance and bias. 

High Variance, low bias = around right answer, but with a lot of spread

Low variance and low bias --> true function

#### Analysis of Squarred Error
$$E[(y - f_{\Theta}(x))^2] = Obs.Var. + (Bias)^2 + Mod. Var $$

$$Noise + (Bias)^2 + Variance$$