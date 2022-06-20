#### 1-D Convolution: Equation
$$x(t) * w(t) = \sum_{\tau} x(t+\tau) w(\tau) $$

#### 1-D Convolution with Features
- Input is T x D( T = # of time steps, D = # of input features)
- Output is T x M (M = # of output features)
- Then W (the filter) has the shape T' x D x M (where T' << T)
- 
$$y(t,m) = \sum_{\tau} \sum_{d=1}^D x(t+\tau,d) w(\tau,d,m) $$

![image](https://user-images.githubusercontent.com/15355357/174596939-97f09dec-5446-4188-9eaa-ec80433d686f.png)

![image](https://user-images.githubusercontent.com/15355357/174596880-f750d9d8-462b-4268-b15f-f1e9176db784.png)

![image](https://user-images.githubusercontent.com/15355357/174596785-fa0e18cd-d58d-4827-a5de-9f7352aa10ac.png)

![image](https://user-images.githubusercontent.com/15355357/174597084-e4b46e57-4e90-4f87-aea6-ea9be3fa72c5.png)

