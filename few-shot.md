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


