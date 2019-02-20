# Intro to Optimization for Data Science
## Lecture 14
### 3/1

For Loss and Minimization, if the derivative = 0 at n, then n is a ***global minimizer***

As long as the function is differentiable, it is convex if the tangent lies below the function at any given point 

Therefore, tangent line at minimizer means every point is above the tangent line 

Thus, if the **Loss Function** is convex and differentiable
L = loss function

$$L(x) + L'(x)(theta - x) <= L(theta)$$

meaning the tangent at theta lies below the value of the function 

### Gradient Descent 
The Gradient point in direction of steepest ascent, to the minimizer. Moves perpendicular to level curves 

