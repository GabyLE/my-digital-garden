---
{"dg-publish":true,"permalink":"/data-scientist/gain-and-lift-charts/","created":"2023-11-17T05:08:02.302-05:00","updated":"2024-03-02T09:32:57.438-05:00"}
---


- Checking the rank ordering of the probabilities.
-  Construction:
1. Calculate the probability for each observation
2. Rank these probabilities in decreasing order.
3. Build deciles with each group having almost 10% of the observations.
4. Calculate the response rate at each decile for Good (Responders), Bad (Non-responders), and total.
## Cumulative gains
### Construction
1. Order all the observations according to the output of the model. 
2. On the left hand side are observations with the highest probability to be target according to the model.
3. On the right hand side are observations with the lowest probability to be target. 
4. On the horizontal axis of the cumulative gains curve, it is indicated which percentage of the observations is considered. 
5. On the vertical axis, the curve indicates which percentage of all targets is included in this group.
For instance, at 30%, the 30% observations with the highest probability to be target is considered.  If the cumulative gains is 70% at 30%, it means that when taking the top 30% observations with highest probability to be target, this group contains already 70% of all targets.

![](https://i.imgur.com/3QjmaWS.png)
### Compare
- The more the line is situated to the upper left corner, the better the model.
- If the lines cross each other, it is not straightforward to decide which model is best.
	- In this case, for instance, you could say that model 2 is better to distinguish the top 10% observations from the rest, while model 1 is better to distinguish the top 70% of the observations from the rest.
![](https://i.imgur.com/pyiYG8o.png)
### Python
- Module: `scikitplot`
```python
import scikitplot as skplt
import matplotlib.pyplot as plt

skplt.metrics.plot_cumulative_gain(true_values, predictions)
plt.show()
```
>Note that predictions should have both the predictions for the target to be 1 as well as the target to be 0.

The output of this piece of code is given here. Observe that there are two curves, the one that we are interested in is the curve for class one, as **we want to predict targets**.
![](https://i.imgur.com/8xlAptZ.png)

## Lift Curve
### Construction
![](https://i.imgur.com/4rCvp0w.png)
1. Order all the observations according to the model. 
2. On the horizontal axis of the lift curve, you indicate **which percentage of the observations is considered**. 
3. On the vertical axis, the lift curve indicates **how many times more than average targets are included in this group**. 

Consider for instance the lift at 10%, and assume that the top 10% observations contains 20% targets. If the average percentage of targets is 5%, the lift is 4, because 20% is 4 times 5%. As another example, consider the lift at 50%, and assume that the top 50% observations contains 10% targets. As 10% is 2 times 5%, the average percentage of targets, the lift is 2 at 50%. A random model has a more or less equal percentage of targets for each group, and therefore the baseline is 1.
### Compare
- Better models have higher lifts. Therefore, curves that are higher, have better accuracy. 
- Lift curves of different models can cross each other. 
  Consider the example given here: model 2 is higher at 10%, but model 1 is higher at 80%. In that case it is hard to say which model is best, as it depends on the situation. If you can target 10% of the population, model 2 is better suited because you can reach more targets, whereas model 1 is better if you want to target a larger part of the population.
![](https://i.imgur.com/podf9jU.png)
### Python
- Modules: `scikitplot` and `matplotlib`
```python
import scikitplot as skplt
import matplotlib.pyplot as plt

skplt.metrics.plot_lift_curve(true_values, predictions)
plt.show()
```
**Output**
![](https://i.imgur.com/01JB9Qr.png)

## Related
[[Data Scientist/Model Evaluation Metrics\|Model Evaluation Metrics]]
[[Data Scientist/Data Scientist\|Data Scientist]]