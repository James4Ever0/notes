---
title: trainable bezier curve multiparameter regressor
created: '2022-09-18T13:57:31.469Z'
modified: '2022-09-18T14:16:29.947Z'
---

# trainable bezier curve multiparameter regressor

first, we need a bezier curve connects (0,0) and (1,1)

```python
def besizeCurve(input_value:float, start=(0,0), end=(1,1), skew=0):
  input_start, output_start = start[0]
  input_end, output_end = end
  assert input_start <= input_value
  assert input_end >= input_value
  return result

```

then, we define our very recursive or flexible regressor:

```python
def multiParameterExponentialNetwork(*args, input_bias=0.1, function=bezierCurve, function_kwargs = {'start':(0,0),'end':(1,1)'skew':0}):
  value = function(input_bias,**function_kwargs)
  for index, input_value in enumerate(args):
    apply_list = [input_value]*(index+1)
    for apply_item in apply_list:
      value += (1-value)*function(apply_item, **function_kwargs)
  return value

```
