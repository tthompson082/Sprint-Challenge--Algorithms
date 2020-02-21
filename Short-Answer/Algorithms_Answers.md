#### Please add your answers to the **_Analysis of Algorithms_** exercises here.

## Exercise I

a)

```python
a = 0 # 0(1)
while (a < n * n * n) #0(n)
    a = a + n * n #0(1)
```

The first line is always constant so it will be 0(1). The while loop is 0(n) because it will run n number of times. For example if n = 1 it will run 1 time, if n = 2 it will run 2 times, etc. The third line is also constant as it is a single expression and will not change in complexity based on whatever n is. To get the overall complexity we start be multiplying the complexity of the loop by its body or 0(n) _ 0(1) to get 0(1 _ n) which simplifies to 0(n). Then we can add 0(n) and 0(1), or 0(n + 1), in which we can drop the constant and keep the dominant term to end up with 0(n).
b)

```python
sum = 0 #0(1)
for i in range(n): #0(n)
    j = 1 #0(1)
    while j < n: #0(n)
        j *= 2 #0(1)
        sum += 1 #0(1)
```

We start by adding the lines in the while loop to get 0(1 + 1), or 0(2). That we can then multiply by the complexity of the while loop resulting in 0(n _ 2) or 0(2n). That can be added to the constant within the for loop to result in 0(2n + 1) which we can then multiply by the complexity of the for loop. That results in 0(n _ (2n + 1)). Finally we can add the constant on line 1 to get 0((n _ (2n + 1)) + 1).
(n _ (2n + 1)) + 1
(2n^2 + 1n) + 1
We can choose the dominant from these which is (2n^2 + 1n). Once again between these we can choose the dominant which is (2n^2). From that we can drop the constant to get a runtime complexity of 0(n^2).
c)

```python
def bunnyEars(bunnies):
    if bunnies == 0: #0(1)
        return 0 #0(1)
    return 2 + bunnyEars(bunnies-1) #0(n)
```

We can treat a recursive function similar to a for loop when calculating runtime complexity. The whole function itself can be treated as the body and then multiplied by the complexity of the recursion itself. As the function will be called as many times as n is passed in for bunnies it will be 0(n). The rest of the body of the function is constant which results in 0(n \* (1 + 1)) which can be simplified to 0(2n). We then drop the constant for the overall runtime complexity of 0(n).

## Exercise II

This sounds like a problem that could best be solved by implementing a binary search. That could result in the fewest possible broken eggs while also running quickly. To start we would split the n-story building in half so that we have an upper half, lower half, and middle floor.

We could then check to see if the egg is broken when dropped from the middle floor. If it is we would then move to the lower half otherwise we would move to the upper half. Then we would repeat the process of splitting that half in half with an upper half, lower half, and middle floor. Repeat the process of dropping the egg to see if it breaks and moving to your new upper or lower half as required. This process would be repeated until there is only 1 floor left.

9
8
7
6
5 - Middle Floor (egg doesn't break)
4
3
2
1

Move to the upper half

9
8
7 - Middle Floor (egg breaks)
6

Move to the lower floor

6 - The egg doesn't break. This is the highest floor you can drop an egg and it not break.

There is the potential to have fewer eggs break if you were to start with a loop from the lowest floor moving to the highest floor 1 at a time dropping an egg from each floor. You could break out of the loop anytime that an egg breaks giving you the highest floor you could drop the egg from. However, this would be much slower for a larger building and it would require quite a few more eggs to be dropped overall. That solution would have a runtime complexity of 0(n) versus the runtime complexity of 0(logn) for our solution. We arrive at 0(logn) by making n smaller each time. The first time there are 9 floors, then 4, then 1. As opposed to n always being 9 floors.
