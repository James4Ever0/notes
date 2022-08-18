---
created: 2022-03-31T02:10:00+08:00
modified: 2022-03-31T02:19:43+08:00
---

# Logic Optimizer for Different Models

For a sequence of models, use classic logic solver to find best logic combination.

select model 0.

select model 1 with 0, iterate through 16 different situations(0, not 0, 1, not 1, 0 and 1, 0 or 1, 0 and not 1, 0 or not 1, not 0 and 1,not 0 or 1, not 0 and not 1, not 0 or not 1), choose the best one. mark it as model A.

select model 2, use the same optimizer to generate model B.

finally iterate through all models. generte model X as a combination of best logic models.
