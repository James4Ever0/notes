---
tags: [model, optimization, trial and error]
title: Logic Optimizer for Different Models
created: '2022-03-30T18:10:00.000Z'
modified: '2022-08-18T14:58:29.700Z'
---

# Logic Optimizer for Different Models

currently we can use hyperopt as the online optimizer. of course for offline optimization there's better option or prediction for it.

For a sequence of models, use classic logic solver to find best logic combination.

select model 0.

select model 1 with 0, iterate through 16 different situations(0, not 0, 1, not 1, 0 and 1, 0 or 1, 0 and not 1, 0 or not 1, not 0 and 1,not 0 or 1, not 0 and not 1, not 0 or not 1), choose the best one. mark it as model A.

select model 2, use the same optimizer to generate model B.

finally iterate through all models. generte model X as a combination of best logic models.
