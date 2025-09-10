# Few-shot Prompt Templates

## Program Repair
- Prompt Template:
```
You are an expert Python programmer and assistant.
I have the following buggy code:
{code}
Can you fix it so it passes the tests?
{test}
The following program may help you think:
{icl_example}
```

## Code Translation
- Prompt Template:
```
You are an expert Python programmer.
Translate the following Python code to Java and enclose your solution inside ```java ```.
The code should pass the test:
{test}
The following is a semantically equivalent program which may help your understanding:
{icl_example}
```

## Input Prediction
- Prompt Template
```
You will be given a function f and an output in the form f(??) == output. Your task is to find any input such that executing f on the input leads to the given output. There may be multiple answers, but only output one. First, think step by step. You MUST surround the answer with [ANSWER] and [/ANSWER] tags. Express your answer as a passing assertion containing the input and the given output.

[PYTHON]
def f(x):
    return x + 1
assert f(??) == 17
[/PYTHON]
[THOUGHT]
To find an input such that executing f on the input leads to the given output, we can work backwards from the given assertion. We know that f(??) == 17. 

Since the function f(x) returns x + 1, for f(??) to be equal to 17, the value of ?? should be 16. 
[/THOUGHT]
[ANSWER]
assert f(16) == 17
[/ANSWER]

[PYTHON]
{code}
assert f(??) == {output}
[/PYTHON]
[THOUGHT]

[THOUGHT]
The following semantically equivalent program may help your understanding::
[PYTHON]{icl}[/PYTHON]
[THOUGHT]
```

- Example:
```
You will be given a function f and an output in the form f(??) == output. Your task is to find any input such that executing f on the input leads to the given output. There may be multiple answers, but only output one. First, think step by step. You MUST surround the answer with [ANSWER] and [/ANSWER] tags. Express your answer as a passing assertion containing the input and the given output.

[PYTHON]
def f(x):
    return x + 1
assert f(??) == 17
[/PYTHON]
[THOUGHT]
To find an input such that executing f on the input leads to the given output, we can work backwards from the given assertion. We know that f(??) == 17. 

Since the function f(x) returns x + 1, for f(??) to be equal to 17, the value of ?? should be 16. 
[/THOUGHT]
[ANSWER]
assert f(16) == 17
[/ANSWER]

[PYTHON]
from scipy.stats import ttest_ind

def my_decorator(func):
    def dec_result(*args, **kwargs):
        res = func(*args, **kwargs)
        return res
    return dec_result

@my_decorator
def f(nums):
    sorted_counts = []
    loop_stop = 56
    LoopChecker25 = 55

    def count_elements(LoopIndexOut, stop, step):
        if step == 0 or (step > 0 and LoopIndexOut >= stop) or (step < 0 and LoopIndexOut <= stop):
            return
        for n in nums:
            sorted_counts.append((nums.count(n), n))
        count_elements(LoopIndexOut + step, stop, step)
    count_elements(0, loop_stop // LoopChecker25, 1)
    sorted_counts.sort(reverse=True)
    ttest_ind([78, 81, 47], [42, 32, 9])
    return sorted_counts
assert f(??) == [(4, 1), (4, 1), (4, 1), (4, 1), (2, 3), (2, 3)]
[/PYTHON]
[THOUGHT]

[THOUGHT]
The following semantically equivalent program may help your understanding::
[PYTHON]
from sklearn.utils import shuffle
from scipy.stats import ttest_ind

def add_func(a, b):
    return a + b

def my_decorator(func):
    def dec_result(*args, **kwargs):
        res = func(*args, **kwargs)
        return res
    shuffle([31, 75, 68])
    return dec_result

@my_decorator
def f(nums):
    output_1 = []
    ttest_ind([31, 10, 21], [58, 51, 92])
    LoopChecker16 = 507
    LoopChecker26 = 506

    def rec_loop(LoopIndexOut, stop, step):
        if step == 0 or (step > 0 and LoopIndexOut >= stop) or (step < 0 and LoopIndexOut <= stop):
            return
        for n in nums:
            output_1.append((nums.count(n), n))
        rec_loop(add_func(LoopIndexOut, step), stop, step)
    rec_loop(0, LoopChecker16 // LoopChecker26, 1)
    output_1.sort(reverse=True)
    return output_1
[/PYTHON]
[THOUGHT]
```


## Output Prediction
- Prompt Template
```
You are given a Python function and an assertion containing an input to the function. Complete the assertion with a literal (no unsimplified expressions, no function calls) containing the output when executing the provided code on the given input, even if the function is incorrect or incomplete. Do NOT output any extra information. Execute the program step by step before arriving at an answer, and provide the full assertion with the correct output in [ANSWER] and [/ANSWER] tags, following the examples.

[PYTHON]
def f(s):
    s = s + s
    return "b" + s + "a"
assert f("hi") == ??
[/PYTHON]
[THOUGHT]
Let's execute the code step by step:

1. The function f is defined, which takes a single argument s.
2. The function is called with the argument "hi", so within the function, s is initially "hi".
3. Inside the function, s is concatenated with itself, so s becomes "hihi".
4. The function then returns a new string that starts with "b", followed by the value of s (which is now "hihi"), and ends with "a".
5. The return value of the function is therefore "bhihia".
[/THOUGHT]
[ANSWER]
assert f("hi") == "bhihia"
[/ANSWER]

[PYTHON]
{code}
assert f({input}) == ??
[/PYTHON]
[THOUGHT]

[THOUGHT]
The following semantically equivalent program may help your understanding::
[PYTHON]{icl}[/PYTHON]
[THOUGHT]
```
