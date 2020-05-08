<h1>Table of Contents<span class="tocSkip"></span></h1>
<div class="toc"><ul class="toc-item"><li><span><a href="#S01---Part-A" data-toc-modified-id="S01---Part-A-1"><span class="toc-item-num">1&nbsp;&nbsp;</span>S01 - Part A</a></span></li><li><span><a href="#S01---Part-B" data-toc-modified-id="S01---Part-B-2"><span class="toc-item-num">2&nbsp;&nbsp;</span>S01 - Part B</a></span></li><li><span><a href="#S02---Part-A" data-toc-modified-id="S02---Part-A-3"><span class="toc-item-num">3&nbsp;&nbsp;</span>S02 - Part A</a></span></li><li><span><a href="#S02---Part-B" data-toc-modified-id="S02---Part-B-4"><span class="toc-item-num">4&nbsp;&nbsp;</span>S02 - Part B</a></span></li><li><span><a href="#S03---Part-A" data-toc-modified-id="S03---Part-A-5"><span class="toc-item-num">5&nbsp;&nbsp;</span>S03 - Part A</a></span></li><li><span><a href="#S03---Part-B" data-toc-modified-id="S03---Part-B-6"><span class="toc-item-num">6&nbsp;&nbsp;</span>S03 - Part B</a></span></li><li><span><a href="#Level-Up---Part-A" data-toc-modified-id="Level-Up---Part-A-7"><span class="toc-item-num">7&nbsp;&nbsp;</span>Level Up - Part A</a></span></li><li><span><a href="#Level-Up---Part-B" data-toc-modified-id="Level-Up---Part-B-8"><span class="toc-item-num">8&nbsp;&nbsp;</span>Level Up - Part B</a></span></li><li><span><a href="#Level-Up---Part-C" data-toc-modified-id="Level-Up---Part-C-9"><span class="toc-item-num">9&nbsp;&nbsp;</span>Level Up - Part C</a></span></li></ul></div>

# Necessary Goals
You will
- Section01
    - a. create a word counts dictionary
    - b. find most common word
- Section02
    - a. calculate the mean and standard deviation of the word counts
- Section03
    - write a function that takes in a parameter to complete a task
    - write a function that takes in multiple parameters to complete a task

# Level Up Goals
- write a function that solves a particular logical task
- write a lambda function to complete a task


```python
# just run this cell
from importlib import reload
import solutions.solutions as sol
reload(sol)
```




    <module 'solutions.solutions' from 'C:\\Users\\Girls Club\\Flatiron\\Module_1\\sections01-section03-assessment\\solutions\\solutions.py'>



# Section 01: Strings
Using the variable `lyrics` below, please solve the following questions


```python
# this cell will just load and open the lyrics
# just run this cell
with open("data/lyrics.txt", "r") as f:
    lyrics = f.read()
lyrics
import string
```

## S01 - Part A
create a dictionary called `word_counter` that counts the number of words in `lyrics`.
- remove all puntuation using `string punctuation`
- lowercase the entire string
- split by `" "`


```python
# build your word_counter here
# Your code here
word_counter = {}
def solution(x):
    lyrics_clean = x.replace('\n', ' ')

    punctuation = string.punctuation
    for x in punctuation:
        for char in lyrics_clean:
            if x == char:
                lyrics_clean.replace(x, '')

    lyrics_clean = lyrics_clean.replace('(', '').replace(')', '').replace(',', '').replace("'", '').replace('[', '').replace(']', '').replace('-', '')
    lyrics_clean = lyrics_clean.lower()
    lyrics_clean = lyrics_clean.split(" ")

    for word in lyrics_clean:
        if word in word_counter:
            word_counter[word] += 1
        else: 
            word_counter.update({word:1})
solution(lyrics)
print(word_counter)
```

    {'shell': 8, 'only': 2, 'come': 2, 'out': 15, 'at': 2, 'nights': 1, 'the': 8, 'lean': 1, 'and': 4, 'hungry': 1, 'type': 1, 'nothing': 1, 'is': 5, 'new': 1, 'ive': 1, 'seen': 1, 'her': 2, 'here': 25, 'before': 1, 'watching': 2, 'waiting': 2, 'ooh': 3, 'shes': 15, 'sittin': 1, 'with': 1, 'you': 10, 'but': 2, 'eyes': 1, 'are': 1, 'on': 1, 'door': 1, '': 6, 'so': 1, 'many': 1, 'have': 1, 'paid': 1, 'to': 1, 'see': 1, 'what': 2, 'think': 1, 'youre': 2, 'gettin': 1, 'for': 2, 'free': 1, 'woman': 2, 'wild': 2, 'a': 15, 'shecat': 1, 'tamed': 1, 'by': 1, 'purr': 1, 'of': 1, 'jaguar': 1, 'moneys': 1, 'matter': 2, 'if': 2, 'in': 2, 'it': 1, 'love': 1, 'aint': 1, 'gonna': 1, 'get': 1, 'too': 1, 'far': 1, 'ohoh': 19, 'she': 26, 'comes': 24, 'watch': 13, 'boy': 7, 'chew': 6, 'up': 6, 'maneater': 12, 'i': 3, 'wouldnt': 1, 'were': 1, 'know': 1, 'can': 1, 'do': 1, 'deadly': 1, 'man': 1, 'could': 1, 'really': 1, 'rip': 1, 'your': 1, 'world': 1, 'apart': 1, 'mind': 1, 'over': 1, 'beauty': 1, 'there': 1, 'beast': 1, 'heart': 1, 'instrumental': 1, 'interlude': 1, 'ooooooooh': 1, 'whoaoh': 1, 'night': 1, 'oohoh': 2, 'whoooa': 1, 'oh': 2, 'yeah': 2}
    


```python
# get actual word_counter here
# just run this cell

word_counter_test = sol.section1_partA(lyrics)
word_counter_test
```




    {'shell': 8,
     'only': 2,
     'come': 2,
     'out': 15,
     'at': 2,
     'nights': 1,
     'the': 8,
     'lean': 1,
     'and': 4,
     'hungry': 1,
     'type': 1,
     'nothing': 1,
     'is': 5,
     'new': 1,
     'ive': 1,
     'seen': 1,
     'her': 2,
     'here': 25,
     'before': 1,
     'watching': 2,
     'waiting': 2,
     'ooh': 3,
     'shes': 15,
     'sittin': 1,
     'with': 1,
     'you': 10,
     'but': 2,
     'eyes': 1,
     'are': 1,
     'on': 1,
     'door': 1,
     '': 6,
     'so': 1,
     'many': 1,
     'have': 1,
     'paid': 1,
     'to': 1,
     'see': 1,
     'what': 2,
     'think': 1,
     'youre': 2,
     'gettin': 1,
     'for': 2,
     'free': 1,
     'woman': 2,
     'wild': 2,
     'a': 15,
     'shecat': 1,
     'tamed': 1,
     'by': 1,
     'purr': 1,
     'of': 1,
     'jaguar': 1,
     'moneys': 1,
     'matter': 2,
     'if': 2,
     'in': 2,
     'it': 1,
     'love': 1,
     'aint': 1,
     'gonna': 1,
     'get': 1,
     'too': 1,
     'far': 1,
     'ohoh': 19,
     'she': 26,
     'comes': 24,
     'watch': 13,
     'boy': 7,
     'chew': 6,
     'up': 6,
     'maneater': 12,
     'i': 3,
     'wouldnt': 1,
     'were': 1,
     'know': 1,
     'can': 1,
     'do': 1,
     'deadly': 1,
     'man': 1,
     'could': 1,
     'really': 1,
     'rip': 1,
     'your': 1,
     'world': 1,
     'apart': 1,
     'mind': 1,
     'over': 1,
     'beauty': 1,
     'there': 1,
     'beast': 1,
     'heart': 1,
     'instrumental': 1,
     'interlude': 1,
     'ooooooooh': 1,
     'whoaoh': 1,
     'night': 1,
     'oohoh': 2,
     'whoooa': 1,
     'oh': 2,
     'yeah': 2}




```python
# Test your code here

# just run this cell

try:
    assert word_counter==word_counter_test
    print('test passed')
except Exception as e:
    print("word_counter does not equal word_counter_test")

```

    test passed
    

## S01 - Part B


```python
# Find the word with the highest counts
# Your code here


sorted_words = sorted(word_counter.items(), key = lambda x : x[1])
most_common_word = sorted_words[-1][0]



```


```python
# get actual most_common_word
# just run this cell

most_common_word_test = sol.section1_partB(lyrics)
```


```python
# test your solution here
# just run this cell

try:
    assert most_common_word==most_common_word_test
    print('test passed')
except Exception as e:
    print("most_common_word does not equal most_common_word_test")
```

    test passed
    

# Section 02: Mean and Standard Deviation
using the dictionary `word_counter` from above, solve the following problems

## S02 - Part A


```python
# calculate the mean word counts
# Your code here
# you can write a function or just do it outright. 

mean_word_counts = None

values = word_counter.values()
mean_word_counts = sum(values) / len(values)
```


```python
# get actual mean word counts
# just run this cell

mean_word_counts_test = sol.section2_partA(lyrics)
```


```python
# test your solution here
# just run this cell

try:
    assert mean_word_counts==mean_word_counts_test
    print('test passed')
except Exception as e:
    print("mean_word_counts does not equal mean_word_counts_test")
```

    test passed
    

## S02 - Part B


```python
# calculate the standard deviation of the word_counts
# you can write a function or just calculate it out right.  It's up to you.
# Your code here
import numpy as np
std_word_counts = np.std(list(values))
std_word_counts = round(std_word_counts, 13)
```


```python
# get actual standard deviation of word counts
# just run this cell

std_word_counts_test = sol.section2_partB(lyrics)
std_word_counts_test = round(std_word_counts_test, 13)
std_word_counts_test
```




    5.2021577117911




```python
# test your solution here
# just run this cell

try:
    assert std_word_counts==std_word_counts_test
    print('test passed')
except Exception as e:
    print("std_word_counts does not equal std_word_counts_test")
```

    test passed
    

# Section03 - Functions

## S03 - Part A


```python
# Your code here
# write the function below
def transform_odds(lst):
    """
    this function should count
    the number of odds in a list
    then do the following calculation for every odd
    - multiply each odd by 3
    - add 1 to each odd number
    return the sum of all of these numbers
    """
    total = 0
    for num in lst:
        if num % 2 != 0:
            total += num*3 + 1
    return total
    pass
```


```python
# run cell to generate a list of 100 random numbers
# just run this cell

import random
random_nums = [random.randint(0, 1000) for i in range(100)]
```


```python
# run this cell to transform the random_numbers and store them to transformed_odds
# just run this cell

transformed_odds = transform_odds(random_nums)
print(transformed_odds)
```

    74964
    


```python
# run this cell to get the actual value of transformed odds
# just run this cell

transformed_odds_test = sol.section3_partA(random_nums)
```


```python
# test your solution here
# just run this cell

try:
    assert transformed_odds==transformed_odds_test
    print('test passed')
except Exception as e:
    print("transformed_odds does not equal transformed_odds_test")
```

    test passed
    

## S03 - Part B


```python
# Your code here
# write a function that checks the numbers in a list numbers
# and checks if any of the numbers are divisible in a list of divisors divisors
# it should return the all numbers in order they're given in the list 
# as a string

def find_if_divisible(numbers, divisors):
    """
    Example: 
    find_if_divisible([10, 19, 15, 20, 23, 30, 50, 100], [2, 8, 5])
    should return 
    "1015203050100"
    
    since all of these numbers are divisible by at least one number in the divisors list
    """
    nums = ''
    for num in numbers:
        for div in divisors:
            if num % div == 0:
                nums += str(num)
                break
    return nums
    
```


```python
# run this cell to get a random set of numbers and divisors
# just run this cell

numbers = [random.randint(0, 50) for i in range(200)]
divisors = [random.randint(1, 20) for i in range(5)]
```


```python
# get your solution for the random numbers above
# just run this cell

number_string = find_if_divisible(numbers=numbers, divisors=divisors)
print(number_string)
```

    4444274024454833361588142445101452235834364612163242105035225020233345321032103527254039824615262048361292620451510122825321628383530253244353950441532015528168522010626272836433304434382524282423327533351548464038261833184252824241822253
    


```python
# get the actual solution for the random numbers above
# just run this cell

number_string_test = sol.section3_partB(numbers, divisors)
```


```python
# test your solution here
# just run this cell

try:
    assert number_string==number_string_test
    print('passed test')
except Exception as e:
    print("number_string does not equal number_string_test")
```

    passed test
    

# Level Up (Optional) Problems

## Level Up - Part A


```python
# Your code here

def is_prime(n):
    """
    write a function that determines if a number is prime
    return True if n is prime else return False
    
    a number, n, is prime if the only divisors of the number are 1 and n 
    """
    for i in range(2, n):
        if n % i == 0:
            return False
            pass
        elif:
            continue
            return True
        
    
```


      File "<ipython-input-287-4d68e929a35c>", line 14
        elif:
            ^
    SyntaxError: invalid syntax
    



```python
# run all tests in this cell
# just run this cell

random_nums = [random.randint(5, 50) for i in range(10)]
for n in random_nums:
    actual_result = is_prime(n)
    expected_result = sol.levelUp_partA(n)
    try:
        assert expected_result==actual_result
        print('test passed')
    except Exception as e:
        print("expected_result does not equal actual_result")
        print(f"{n}  is {'NOT'*(1-expected_result)} prime but you returned {actual_result}")
```

    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    test passed
    

## Level Up - Part B


```python
# complete this function
# Your code here

def find_common_elements(lst1, lst2):
    """
    write a function that returns a set
    of all of the elements that are in both
    lst 1 and lst2
    
    Example
    input:
       - lst1 = [2, 3, 5, 3, 5, 3]
       - lst2 = [3, 5, 6]
       
    return:
       - (3, 5)
    """
    lst3 = []
    for x in lst1:
        for y in lst2:
            if x == y:
                lst3.append(x)
    return set(lst3)
```


```python
# run the following tests
# just run this cell

for i in range(10):
    lst1 = [random.randint(0, 100) for i in range(random.randint(15, 20))]
    lst2 = [random.randint(0, 100) for i in range(random.randint(15, 20))]
    actual_result = find_common_elements(lst1, lst2)
    expected_result = sol.levelUp_partB(lst1, lst2)
    try:
        assert expected_result==actual_result
        print('test passed')
    except Exception as e:
        print("expected_result does not equal actual_result")
    print(find_common_elements(lst1, lst2))
```

    test passed
    {40, 73, 54}
    test passed
    {48, 80, 94}
    test passed
    {17, 51, 22}
    test passed
    {42, 34, 87}
    test passed
    {61}
    test passed
    {2, 79}
    test passed
    {71}
    test passed
    {45, 18, 54, 56, 58}
    test passed
    {62, 48, 100, 30}
    test passed
    {80, 97, 20}
    

## Level Up - Part C


```python
# write a lambda function called rng that returns the range of a list of numbers
# Your code here
rng = lambda x: abs(max(x)) - abs(min(x))

```


```python
# run these tests
# just run this cell

# this cell goes through 2 tests. 
# 1. did you write a function called rng that is actually a lambda function
# 2. is written correctly
try:
    assert '<lambda>'==rng.__name__
    print("rng is a lambda function! great work so far")
    print("running 10 random tests now")
    print("-"*50)
    for i in range(10):
        lst = [random.randint(-1000, 1000) for i in range(random.randint(10, 20))]
        actual_range = rng(lst)
        expected_range = sol.levelUp_partC(lst)
        print(rng(lst))
        print(sol.levelUp_partC(lst))
        try:
            assert actual_range==expected_range
            print('test passed, ranges are equal')
        except:
            print("expected_result does not equal actual_result")
    
except:
    print("rng is not a lambda function, must be a lambda function to continue")
```

    rng is a lambda function! great work so far
    running 10 random tests now
    --------------------------------------------------
    98
    1822
    expected_result does not equal actual_result
    317
    1523
    expected_result does not equal actual_result
    -185
    1771
    expected_result does not equal actual_result
    -1
    1823
    expected_result does not equal actual_result
    -29
    1829
    expected_result does not equal actual_result
    -314
    1614
    expected_result does not equal actual_result
    -49
    1469
    expected_result does not equal actual_result
    46
    1640
    expected_result does not equal actual_result
    97
    1889
    expected_result does not equal actual_result
    671
    1303
    expected_result does not equal actual_result
    


```python
# Convert this notebook to README by running this cell!
!jupyter nbconvert --to markdown assessment.ipynb && mv assessment.md README.md
```

    [NbConvertApp] Converting notebook assessment.ipynb to markdown
    [NbConvertApp] Writing 16093 bytes to assessment.md
    


```python

```
