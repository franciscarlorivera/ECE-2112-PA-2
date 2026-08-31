# ECE-2112-PA-2
**EXPERIMENT 2: NUMERICAL PYTHON (NUMPY)**

Rivera, Francis Carlo E. | 2ECE-D

The repository covers Programming Assignment 2 for our ECE2112: Advanced Computer Programming and Algorithms course. The PA contains three programming problems that focuses on constructing NumPy arrays and using NumPy operations to perform mathematical array operations as well as array manipulation to achieve the desired results in each problem.

### INTENDED LEARNING OUTCOMES
1. create and reshape NumPy arrays using appropriate NumPy functions
2. perform vectorized numerical operations on an ndarray
3. compute array statistics and use Boolean conditions to select elements
4. save computed NumPy arrays as .npy files

# A. REPRODUCIBLE NORMALIZATION PROBLEM
> Objectives:
> - Create a reproducible random 5 × 5 integer ndarray named **"X"** and obtain the mean (x̄) and standard deviation (σ) of all 25 elements in the array.
> - Normalize the array using the formula **"Z = (X-x̄)/σ"** and store the normalized array in **"X_normalized"**.
> - Display **"X, X normalized, its mean, and its standard deviation"**, wherein the normalized mean must be 0 and the normalized standard deviation must be 1.
> - Save the normalized array as **"X_normalized.npy"**.

The following operations were utilized in constructing and manipulating arrays, as well as performing array operations:
- `import numpy as np` ---> Imports the Numerical Python library that gives access to array structures as well as allowing operations and data manipulation to be performed on arrays. The code also shortens the name of the library to np.
- `np.random.seed(2112)` ---> Code that ensures the exact sequence of randomized numbers are obtained everytime the code is executed.
- `X = np.random.randint(10, 101, size=(5, 5))` ---> Creates a 2D array in the shape of a 5x5 matrix where the elements are random generated integers within the range of 10 to 100. The array is assigned to the variable X.
- `np.mean(X)` ---> Obtains the mean of all elements within the array X.
- `np.std(X)` ---> Obtains the population standard deviation of all elements within the array X.
- `X_normalized=(X-np.mean(X))/np.std(X)` ---> Normalizes the array X and stores the elements obtained into a new array called X_normalized. The operation subtracts the X mean from every element of X, which is then divided by the population standard deviation of the array X.
 - `np.mean(X_normalized)` ---> Obtains the mean of all elements within the array X_normalized.
 - `np.std(X_normalized)` ---> Obtains the standard deviation of all elements within the array X_normalized.
 - `print ("X Array:\n", X, "\n")` ---> Displays the array X below the header "X Array" and creates a line break below the matrix to separate the output from other subsequent outputs.
 - `print ("X_normalized Array:\n", X_normalized, "\n")` ---> Displays the array X_normalized below the header "X_normalized Array" and creates a line break below the matrix to separate the output from other subsequent outputs.
 - `print ("X_normalized Mean:", np.mean(X_normalized), "\n")` ---> Displays the mean of the array X_normalized next to the text "X_normalized Mean:" and creates a line break below the output to separate it from other subsequent outputs.
 - print ("X_normalized Standard Deviation:", np.std(X_normalized)) ---> Displays the standard deviation of the array X_normalized next to the text "X_normalized Standard Deviation:" .
 - `np.save('X_normalized.npy', X_normalized)` ---> Saves the normalized array X_normalized as a NumPy file titled "X_normalized.npy".

```
import numpy as np

np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))

X_normalized=(X-np.mean(X))/np.std(X)

np.mean(X_normalized)
np.std(X_normalized)

print ("X Array:\n", X, "\n")
print ("X_normalized Array:\n", X_normalized, "\n")
print ("X_normalized Mean:", np.mean(X_normalized), "\n")
print ("X_normalized Standard Deviation:", np.std(X_normalized))

np.save('X_normalized.npy', X_normalized)
```

# B. CUBES DIVISIBLE BY 4 PROBLEM
> Objectives:
> - Using NumPy, create the first 100 positive integers, cube every element, and reshape the result into a 10 × 10 ndarray named **"C"**. Thus, C begins with 1 and end with 1000000.
> - Use a Boolean condition on C to obtain every cubed value divisible by 4 and store the selected values in the array **"div_by_4"**.
> - Preserve NumPy’s normal row-major selection order.
> - Display **"the shape of C, the array div by 4, and the number of selected elements"**. A correct solution has 50 selected elements; the first is 8 and the last is 1,000,000.
> - Save the selected array as **"above_mean.npy"**.

The following operations were utilized in constructing and manipulating arrays, as well as performing array operations:
- `C=np.arange(1,101)**3` ---> Creates a 1D array assigned to the variable C, wherein the elements contained within the array are the cubes of all positive integers within the range 1 to 100.
- `C.resize(10,10)` ---> Manipulates the shape of the 1D array C into a 2D array in the shape of a 10x10 matrix.
- `div_by_4=C[C%4==0]` ---> Filters the elements contained C and stores the obtained elements into the array div_by_4. The code uses a Boolean condition that obtains every value divisible by 4 by using the modulo operator to see whether or not a value, when divided by 4, returns a remainder of 0.
- `np.shape(C)` ---> Returns the dimensions of the array C.
- `print ("Shape of C:", np.shape(C), "\n")` ---> Displays the shape or dimensions of the array C next to the text "Shape of C:" and creates a line break below the output to separate it from other subsequent outputs.
- `print ("div_by_4 Array:\n", div_by_4, "\n")` ---> Displays the array div_by_4 below the header "div_by_4 Array" and creates a line break below the matrix to separate the output from other subsequent outputs.
- `len(div_by_4)` ---> Obtains the 1D length of the array div_by_4 which in turn counts the total number of elements within the array.
- `print ("Nummber of elements stored in div_by_4:", len(div_by_4))` ---> Displays the total number of elements stored within the array div_by_4 next to the text "Number of elements stored in div_by_4:".
- `np.save('div_by_4.npy', div_by_4)` ---> Saves the selected array div_by_4 as a NumPy file titled "div_by_4.npy".

```
C=np.arange(1,101)**3
C.resize(10,10)

div_by_4=C[C%4==0]

print ("Shape of C:", np.shape(C), "\n")
print ("div_by_4 Array:\n", div_by_4, "\n")
print ("Nummber of elements stored in div_by_4:", len(div_by_4))

np.save('div_by_4.npy', div_by_4)
```

# C. ABOVE-MEAN SQUARES PROBLEM
> Objectives:
> - Create a 6×6 ndarray named **"S"** containing the squares of the first 36 positive integers in increasing
> row-major order.
> - Compute the mean of all elements of S and store it in **"S_mean"**.
> - Use Boolean filtering to select only the elements strictly greater than S_mean and store these values in **"above_mean"**.
> - Display **"S, S mean, above mean, and the number of selected elements"**. A correct solution has 15 selected elements; the first is 484 and the last is 1296.
> - Save the selected array as **"above_mean.npy"**.

The following operations were utilized in constructing and manipulating arrays, as well as performing array operations:
- `S=np.arange(1,37)**2` ---> Creates a 1D array assigned to the variable S, wherein the elements contained within the array are the squares of the first 36 positive integers.
- `S.resize(6,6)` ---> Manipulates the shape of the 1D array S into a 2D array in the shape of a 6x6 matrix.
- `S_mean=np.mean(S)` ---> Obtains the mean of all elements stored in the array S, and stores the value in S_mean.
- `above_mean=S[S>S_mean]` ---> Filters the elements stored in array S and stores the obtained values in the array above_mean. The code uses a Boolean condition that obtains every value greater than the mean of the elements in S using the greater than operator to evaluate if an element, when compared to the mean, has a greater value.
- `print ("S Array: \n", S, "\n")` ---> Displays the array S below the header "S Array" and creates a line break below the matrix to separate the output from other subsequent outputs.
- `print ("Mean of all elements in Array S:", S_mean, "\n")` ---> Displays the mean of all elements in the array S next to the text "Mean of all elements in Array S:" and creates a line break below the output to separate it from other subsequent outputs.
- `print ("above_mean Array: ", above_mean, "\n")` ---> Displays the array above_mean below the header "above_mean Array" and creates a line break below the matrix to separate the output from other subsequent outputs.
- `len(above_mean)` ---> Obtains the 1D length of the array above_mean which in turn counts the total number of elements within the array.
- `print ("Number of elements stored in above_mean:", len(above_mean))` ---> Displays the total number of elements within the array above_mean next to the text "Number of elements stored in above_mean:".
- `np.save('above_mean.npy', above_mean)` ---> Saves the selected array above_mean as a NumPy file titled "above_mean.npy".

```
S=np.arange(1,37)**2
S.resize(6,6)

S_mean=np.mean(S)

above_mean=S[S>S_mean]

print ("S Array: \n", S, "\n")
print ("Mean of all elements in Array S:", S_mean, "\n")
print ("above_mean Array: ", above_mean, "\n")
print ("Number of elements stored in above_mean:", len(above_mean))
```


# VERSION HISTORY
- August 29, 2026: README File created.
- August 29, 2026: Added content for introductory of reposotory; added objectives for part A of PA2.
- August 30, 2026: Added objectives for part B and part C; updated content for parts A, B, and C.
- August 31, 2026: Uploaded Jupyter Notebook file and NumPy files: X_normalized.npy, div_by_4.npy, and above_mean.npy
