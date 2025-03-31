# Overview

This assessment evaluates your ability to perform the following tasks in accordance with ICTPRG547 Apply advanced programming skills in another language:

## Performance elements
- 1.4 Code sorting algorithm using programming techniques
- 3.2 Detect and resolve errors of syntactical, logical and design origin
- 3.3 Design and document required tests
- 4.1 Develop and document solution according to debugging test results

You will demonstrate your performance by providing evidewnce that you can code at least one sorting algorithm, and test and debug the code to resolve errors of a syntactical, logical, or design origin.

To succeed you must use a systematic, analytical processes in complex, non-routine situations, setting goals, gathering relevant information, and identifying, and evaluating, options against the agreed criteria

## General instructions
> CRITICAL: Failure to follow these instructions will lead to an NYC

- Fork this repository before you start work
- Clone the repository to your local machine
- Commit changes after you complete each task
- Push changes to your GitHub repository
- Ensure you submit your git repo along with your assessment submission


## Players have scores now

### Task: Add scores to players

Add a private instance variable to the Player class that will hold the score (a positive integer value).

Provide a getter (property) and a setter method for this value.

#### Success criteria
- [ ] Correct use of private instance variable
- [ ] Use of properties to create a getter and setter
- [ ] Raising ValueError if someone attempts to set a non-positive value

## Sorting players


### Task: Add unit tests for sorting players

Add the following unit tests to the `test_player.py` file:

```python
def test_sort_players(self):
    players = [Player("Alice", uid='01', score=10), Player("Bob", uid='02', score=5), Player("Charlie", uid='03', score=15)]
    # note: ensure initialization code is valid for **your** implementation

    # do **not** change the following code:
    sorted_players = sorted(players)

    # players must be sorted by score as shown here:
    manually_sorted_players == [Player("Bob", uid='02', score=5), Player("Alice", uid='01', score=10), Player("Charlie", uid='03', score=15)]

   self.assertListEqual(sorted_players, manually_sorted_players)

```
> **Note:** f you have made other changes to the initiliazer of your player update the above code to reflect this change - you must not make any other changes to the test code above.

### Task: Interpret unit tests

What was the outcome of running the above unit test, copy paste the output **for just this particular test** below:
```text
Your output here
```

### Success criteria
- [ ] Unit test added to `test_player.py`
- [ ] Unit test output provided
- [ ] Unit test output reflects the error in `sorted(players)` (if you are getting another error read the instructions CAREFULLY)

#### Question:
The tests checks that calling sorted on a list of players will sort them by score, what is the **only** magic method that must be implemented in the player class for the `sorted` function to succeed?

> Answer Here


#### Task: Implement the magic method in the Player class
Add a test case to test_player to test the comparison operator you are about to add - ensure you do not test a dunder method directly!
```python
def test_players_can_be_compared_by_score(self):
    # note: ensure initialization code is valid for **your** implementation
    alice = Player("Alice", uid='01', score=10)
    bob = Player("Bob", uid='02', score=5)

    # Add the appropriate expression to the following assert test
    self.assertTrue(...)
```

Run the test and confirm that your error resembles the previous error

```text
INSERT ERROR OUTPUT HERE
```

Implement the appropriate magic method in the Player class and ensure you pass this test (and only this test!).

#### Success criteria
- [ ] Unit test added to `test_player.py`
- [ ] Magic method implemented in `Player` class
- [ ] Initial Failed Unit test output provided
- [ ] Unit test runs successfully with submited code
- [ ] Dunder method not employed directly

#### Task: Are we sorted yet?

Rerun `test_sort_players` does the test pass? If not, include the output below:

```text
Your output here
```

Why did the test fail (note: if it doesn't fail, it means there is something you have already done before you were asked to - you need to figure out what that is!)?

> Answer here

Add the necessary code to the Player class to ensure that the `test_sort_players` test passes.

#### Success criteria
- [ ] Correct explanation of why `test_sort_players` failed/passed
- [ ] Correct implementation of the magic method in the `Player` class
- [ ] `test_sort_players` passes when run against the submitted code



## Implement a custom sorting algorithm

The senior developer on your team believes that a custom sorting algorithm would be more efficient than the built-in `sorted` function (you grit your teeth, sigh, and realize you need this job!). They have asked you to implement a custom sorting algorithm that will sort a list of players by score.

To help you get started they have provided you with some example code that they wrote in their undergraduate days:

```python
def sort_quickly(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[0]
    left = []
    right = []
    for x in arr[1:]:
        if x < pivot:
            left.append(x)
        else:
            right.append(x)
    return sort_quickly(left) + [pivot] + sort_quickly(right)
```

### Question: complexity
What is the expected time and space complexity of the above algorithm? You can answer using big O or in plain English but in both cases you MUST justify your answer.

> Answer here

### Task: Implement the custom sorting algorithm

#### Create a new method in the Player class
Use the sample above (and its algorithm) as a starting point to implement a `classmethod` in the Player class that takes a list of players and returns a list of players sorted by score in **descending** order. Top scores come first!

#### Create a test cases
Add a seperate test case to `test_player.py` to test your custom sorting algorithm

Include your code below:

```python
# YOUR CUSTOM Sorting here
```
#### Success criteria
- [ ] Custom sorting algorithm implemented in the `Player` class as classmethod
- [ ] Custom sorting algorithm sorts in descending order
- [ ] Custom sorting algorithm compares players using their score (via the rich comparison operators)
- [ ] Custom sorting algorithm tested in `test_player.py` and tests passed


### Test your custom sorting algorithm at scale

The senior developer is impressed with your work and asks you to test your custom sorting algorithm with a list of 1000 players. They provide you with a script that will generate a list of 1000 players with random scores.

```python
import random
from player import Player


players = [Player(f"Player {i}", uid=f"{i:03}", score=random.randint(0, 1000)) for i in range(1000)]
```

#### Task: Create a test case to sort 1000 players

Using the code above as a starting point, create a test case to test your custom sort algorithm - you can test it against the `sorted` function to ensure it is working correctly.

Include your test case below:

```python

```

#### Success criteria

- [ ] Test case added to `test_player.py`
- [ ] Test case sorts 1000 players correctly when compared to `sorted` function
- [ ] Test case passes when run against the submitted code


#### Task: Testing sorting sorted players

You had a scary thought - and decided to test your custom sorting algorithm against a list of players that are already sorted by score. You are worried that your algorithm might not be efficient in this case.

#### Task: Create a test case to sort 1000 sorted players

Create a test case that tries to sort 1000 players that are already sorted.

If you get a failure, include the failure below:

```text
YOUR FAILURE HERE
```

Provide a reason why this test failed (if you got recursion errors, you need to explain **why** they occurred).

If your implementation did not fail, you must explain what changes you made to the original algorithm given by the senior developer to ensure that it did not fail.

> Answer here

Propose a fix to your sorting algorithm that fixes this issue.

```python
# YOUR FIX HERE
# Highlight what the fix was
```

#### Success criteria

- [ ] Test case added to `test_player.py`
- [ ] Test case passes only when changes above are added


## Submit your work
- [ ] Ensure all tests pass
- [ ] Include git with each task committed (you must show at least 5 commits)
- [ ] Push your changes to your GitHub repository

# End of assessment
