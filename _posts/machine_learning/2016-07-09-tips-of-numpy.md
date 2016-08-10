---
layout: post
title: Tips of Numpy
categories: Machine Learning
---

Shuffle Multiple Arrays
-----------------------

Given two identical size of `ndarray`, how to shuffle the two arrays and keep elements of the first array corresponding to the elemenets of the second array?

`Numpy` provides the `ndarray` a special ability, called `index array`. You could put an array in the square bracket, `[]`, to get the permutation.

#### For example

```python
a = np.arange(10) # -> array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
b = a[[3, 2, 1, 4, 5, 6, 9, 8, 7, 0]] # -> array([3, 2, 1, 4, 5, 6, 9, 8, 7, 0])
c = a[[3, 2, 1, 0]] # -> array([3, 2, 1, 0])
```

So you could use `numpy.random.permutation` function to generate the *index array* and use it to shuffle multiple arrays.

#### For example

```python
def randomize(a, b):
    # Generate the permutation index array.
    permutation = np.random.permutation(a.shape[0])
    # Shuffle the arrays by giving the permutation in the square brackets.
    shuffled_a = dataset[permutation]
    shuffled_b = labels[permutation]
    return shuffled_a, shuffled_b
```

Boolean Statements
------------------

Boolean statments are commonly used in combination with the `and` operator and the `or` operator.

#### For example

```python
# Creating an image.
img1 = np.zeros([20, 20]) + 3
img1[4:-4, 4:-4] = 6
img1[7:-7, 7:-7] = 9

# Ley's filter out all values larger than 2 and less than 6.
index1 = img1 > 2
index2 = img1 < 6
compound_index = index1 & index2

img2 = np.copy(img1)
img2[compound_index] = 0
```

The `img1`:

![...](/images/2016-07-09-tips-of-numpy/ex-02-fig-01.png)

The `img2`:

![...](/images/2016-07-09-tips-of-numpy/ex-02-fig-02.png)
