# What is a *Big O*

**Big O asymptotic analysis** is the language and metric we use to describe the efficiency of algorithms.

**Big-O** notation is the language that we use for talking about how long an algorithm takes to run.

<p align="center">
<img src="https://miro.medium.com/max/2928/1*5ZLci3SuR0zM_QlZOADv8Q.jpeg" width="450" height="300" style="display:block">
</p>

As it can be seen on the graph **Big O** depends on how many operations and elements does the algorithm has if the algorithm has so many operations its complexity become more horrible.

## What is a good code

1. Readable
2. Scalable
    * Means how efficient the code is
    * Time or Speed
    * Space or Memory



## Time Complexity (Speed)

Let's say that you want to send big data (1TB) to your friend on the other side of the word.

You can either send using your internet connection or sent with cargo that flies to your friend in a day.

We can describe this data transfer algorithm runtime as:

* *Electronic Transfer:* O(s) where s is the size of the file.
* *Cargo Transfer:* O(1) regardless of the size of the file.

At certain point as the size of the file increases the time for using electronic transfer will surplus the time you spend for cargo transfer.

<img align="left" src="https://i.stack.imgur.com/PWc9I.png" width="250" height="230" style="display:block">

**Most Used Runtimes**
* O(log N)
* O(N log N)
* O(N)
* O(N2)
* 0(2N)

You can also have *multiple variables* in your runtime. 

For example, the time to paint a fence that's _w_ meters wide and _h_ meters high could be described as **O(wh)**. If you needed _p_ layers of paint, then you could say that the time is **O(whp)**.

**Iterating through half a collection is still O(n)**

**Two separate collections: O(a * b)**

### What can cause time in a function?

* Operations (+, -, *, /)
* Comparisons (<, >, ==)
* Looping (for, while)
* Outside Function call (function())


## O(n) Notation Linear Time
```python
everyone = ['dory', 'bruce', 'marlin', 'nemo', 'gill', 'bloat', 'nigel', 'squirt', 'darla', 'hank']

def findNemo(array):
    for name in array:
        if name == 'nemo':
            print('Found Nemo')
    t1 = time.time()
```

<img align="left" src="https://i.imgur.com/DVa5e0R.png" width="250" height="200" style="display:block">



As the number of elements increases, number of operations increase as well; because it loops though the array.

This is called _O(n)_ or _Linear Time_. _n_ means the number of elements. If the number of array is 1 it is _O(1)_, if the number of arras is 10 it is _O(10)_. As the number of elements increases the number of operations increases linearly.

_O(n)_ has a fair complexity as it can be seen above graphs. It is the most common.

## O(1) Notation Constant Time
```python
def getOne(array):
    print(array[0])
```
Every time the algorithm runs it only operate 1 item. So it is _O(1)_

<img align="left" src="https://i.imgur.com/Acyu6hZ.png" width="250" height="200" style="display:block">


If we increase the operation:
```python
def getOne(array):
    print(array[0])
    print(array[1])
```

It becomes _O(2)_.

</br>
</br>

<img align="left" src="https://i.imgur.com/VilZaXJ.png" width="250" height="200" style="display:block">

If the operation become 3 the notation would be _O(3)_, and so on.

But in terms of _scalability_ these all notations are _Constant Time_ which is _O(1)_.

</br>
</br>
</br>

#### Example
* _Find the BigO notation of the algorithm below:_
```python
def funChallange(input):
    a = 10 # O(1)
    a = 50 + 3 # O(1)
    
    for i in Range(len(input)): # O(n)
        anotherFunction() # O(n)
        stranger = True # O(n)
        a+=1 # O(n)
    return a # O(1)
```

* _O(3+3n) is the answer_


#### Example
* _Find the BigO notation of the algorithm below:_
```python
def anotherFunChallenge(input):
    a = 5 # O(1)
    b = 10 # O(1)
    c = 50 # O(1)
    
    for i in range(len(input)): # O(n)
        x = i + 1 # O(n)
        y = i + 2 # O(n)
        z = i + 3 # O(n)
  
    for j in range(len(input)): # O(n)
        p = j * 2 # O(n)
        q = j * 2 # O(n)
  
    whoAmI = "I don't know" # O(1)
```
* O(4+7n) is the answer

_In an interview you do not need to calculate BigO_

### Simplify Rules (There are 4 rules)
1. Worst Case

If we look at the example below;
```python
everyone = ['dory', 'bruce', 'marlin', 'nemo', 'gill', 'bloat', 'nigel', 'squirt', 'darla', 'hank']

def findNemo(array):
    for name in array:
        if name == 'nemo':
            print('Found Nemo')
            break
    t1 = time.time()
```
Nemo is the 4th member so the algorithm operate only 4 times but what is the 'nemo' wa the last element, then the algorithm would run 10 times. Therefore we always need to calculate the worst case.

2. Remove Constants

```python
def printFirstItemThenFirstHalfThenSayHi100Times(items):
    print(items[0]) # O(1)

    middleIndex = round(len(items) / 2)  # O(1)
    index = 0

    while (index < middleIndex):
        print(items[index]) # O(n/2)
        index+=1
    
    for i in range(100):
        print('hi') # O(100)
```
This algorithm is O(102 + n/2) but we could ignore constants like "102" because if n is 1.000.000.000 102 won't matter much and we could also lose the division "n/2" because n/2 will not matter as "n" grows.

**_Because as n grows the increase would still be linear._** So we could say this algorithm is **O(n)** and ignore the constants. In other words _Big O_ does not care how "n" is calculated it consider how "n" changes.

In addition if the algorithm was **_O(2n)_** we still drop the constants and say **O(n)**.

3. Different terms for inputs

> This is the most confusing rule.

```python
def compressBoxes(items1, items2):
    for item in items1:
        print(item)
    for item in items2:
        print(item)
```

On the algorithm below there are two parameters "_item1 and item2_". Both arrays could be different size, therefore we should use different terms for different inputs.

Which means the _Big O_ of this algorithm is **O(a + b)**

## O(n^2) Quadratic Time

```python
arr = ['a','b','c','d','e']

def logAllPairsOfArray(arr):
    for i in arr:
        for j in arr:
            print(i,j)
```
For nested loop algorithms like above we use "n" multiplied by the number of nested loop. For instance:

This algorithm is **_O(n^2)_**


4. Drop Non Dominants

```python
arr = [1,2,3,4,5]

def logAllPairsOfArray(arr):
    print('The Numbers are:')
    for a in arr:
        print(a)
    print('The sum of numbers are:')
    for i in arr:
        for j in arr:
            print(i+j)
```

The **Big O** of this algorithm is _O(n^2 + n)_, to simplify it we could drop the non dominant part of the Big O and say **_O(n^2)_**.

## O(!n) Factorial

> This is the most expensive algorithm and if you using it there most be something with the algorithm.

Factorial algorithm add a loop for every element.

## Space Complexity (Memory)

* **Heap :** is where we store variables.
* **Stack :** where we keep track of our function calls.

### What causes space complexity

* Variables
* Data Structures
* Function Calls
* Allocations

Adding all the above to your algorithm will increase the _Space Complexity_
