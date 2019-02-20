# MODELING AND ESTIMATION
## Lecture 13
### 2/27


A model is an **idealized** representation of a system. A theory of the data generation process from the world.
* build models to make accurate predictions
* provide instight into complex phenomena

**Estimated Model**: An instantiation of the model

**Model Terminology**
* Right skewed: data is weighted more on left side and slopes down on the right
* bimodal: two peaks of equal size
* theta* is considered to be the true constant parameter determined by the universe. We try to estimate from the data.

### Model Estimation Process
1) Define the Model: simplified representation of the world
2) Define the Loss Function: measure how well a particular instance of the model fits the data
  * different loss functions for each record
  * take average loss over entire dataset
3) Minimize the Loss: find the parameter values that minimize the loss on the data 

### Loss Function
* a function that characterizes the cost, error, or loss resulting from a particular choice of model or model parameters (because the model will miss something and we want to miss as little as possible **optimization**)
* choice of loss function depends on the estimation task
  * quantitative variable???
  * qualitative variable????
  * require different approaches
  * result of loss function impacts outliers and amount of error we tolerate due to context
  

### Squared Loss ($$L^2$$ Loss)
$$ L(Θ,y) = (y - Θ)^2 $$
  
Loss between data $$y$$ and paramater $$Θ$$.
  
  
*The difference between data $$y$$ and $$Θ$$ squared is the loss*

* always want positive value
* theta is predicted value
* y is the observed data point
* the loss is the error in the prediction

The above is called an $$L^2$$ Loss
* parabolic
* if Θ is close to y, it is a good fit and represents no loss
* if Θ far from y, lots of loss
* much faster than $$L^1$$
* very sensitive to outlier 


### Absolute Loss ($$L^1$$ Loss)
$$ L(Θ, y) = |y - Θ| $$
* linear 
* always positive
* Θ = y is a good fit and no loss
* Θ far from y is a bad fit represents some loss
* less sensitive to outliers but not smooth 

Absolute value is not differentiable at y = Θ

### Huber Loss
Piecewise function 

* choose parameter *alpha*, when differenc is less than *alpha*, use **Squared Loss** 
* Therefore, close to observation, there is no sharp curve 
* as move away from observation becomes straight line 
* parabala and straight lined are joined so not sharp corner 
* less sensitive to outliers and smooth, but has an extra parameter to deal with 

### Average Loss
define loss by computing average of the loss on each record. Comparing loss of **dataset** not single point. 

$$ L(Θ,D) = 1/n \sum_{i=1}^{n} L(Θ, y_i) $$

In some cases, take weighted average (when certain observations more important than others )

### Minimize a Function
1) take derivative 
2) set equal to 0
3) solve parameters  

*setting equal to 0 will not always give the minimum*

**so take the 2nd derivative**
It is a minimum if function curves up after this point
* first derivative measures slope
* second derivative measures curvature, shape of the surface 

After 2nd derivative
* positive = goes up after, so this is a minimum
* negative = goes down after, so not a minimum
* 0 = at critical point, not min

We are interested in **convex functions** with respect to the parameters Θ 

**Convex Set**
* any line draw between two points on the boundary ever leave the polygon
* equivalently, all angles are <= 180 degrees
* interior is a convex set, boundary is a convex polygon 

**Non-Convex Set**
* can find a line that leaves the set between two points on the boundary 

**Convex Function** 
*  epigaph of function = set of of function above the function (The fill)
* draw line between two points, value is always above or equal the boundary 
* function $$f$$ is convex if and only if:
a, b are two points on the boundary
$$tf(a) + (1 - t)f(b) >= f(ta + (1-t)b)$$

**Minimizing the Average Squared Loss results in the Mean. The mean is the optional choice**

**Minimizing the Average Absolute Loss results in -1 for less than minimizer and +1 for greater than minimizer. Discontiuous. Sin function. Sum over the condition. This is the Median.**
* if median is even, it doesn't really matter what you choose as long as it is between the 2 middle values. may choose bottom or top value, or mean between 2. They are technically equal!

**The process**
1) verify convex function
2) compute the derivative 
3) set derivative equal to 0 and solve for parameters 

L^2 leads to mean, L^1 leads to median

**Huber Loss**
Small alpha: Derivative is continuous, many optima. similar to L^1
Large alpha: unique optimum like squared loss. similar to L^2 




  
  
  
  
  
  
  
  
  
  
  
 