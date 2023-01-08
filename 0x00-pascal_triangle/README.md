<h2>Pascal Triangle</h2>
Pascal Triangle is an arrangement of numbers in rows resembling a triangle with each row consisting of the coefficients in the expansion of (a+b)**n for n=0,1,2,3,…

For Example: 
(a+b)**2 = 1a**2+2ab+1b**2
(a+b)**3=a**3+3a**2b+3ab**2+b3

We have three approaches based on the time and space complexity to execute the Pascal Triangle algorithm and print it. The three approaches are as follows:

O(n**3) time complexity. O(n2) time and O(n2) extra space. O(n**2) time and O(1) extra space.

In all three approaches, we are going to take an integer value as an input that represents the number of rows from the top of the Pascal Triangle to be printed.
```
For example, if the input i = 5, the output will be:

1
11
121
1331
14641
```

Approach 1: Print the Pascal Triangle with 
O(n**3)
 time complexity
In a Pascal Triangle, every single element of every row is calculated by a formula of Combinations which is commonly known as "n choose k" or the number of combinations of k elements from n elements. The formula is:

C(n,k)=(nk)=n!/k!(n−k)!

Note: "n choose k" can also be written C(n,k), nCk or even nCk.

Note that the row number and the column number start from 0.

As, seen in the above table, in the nCk formula:

n = The current row number

k = The current column number

Let's see if the formula works:

3C2=3!/(3−2)!∗2!=3!/(1!∗2!)=(3∗2∗1)/(1∗2∗1)=3

```
def pascalTriangle(num):
    # Iterating through rows
    for n in range(0, num):

        # iterating through each value of the row
        for k in range(0, n + 1):
            print(factFormula(n, k),
                  " ", end="")
        print()

def pascalTriangle(num):
    # Iterating through rows
    for n in range(0, num):

        # iterating through each value of the row
        for k in range(0, n + 1):
            print(factFormula(n, k),
                  " ", end="")
        print()

# Driver code
num = int(input("Enter the number of rows: "))
pascalTriangle(num)
```
```
output

​Enter the number of rows: 5 

1 

1 1 

1 2 1

1 3 3 1 

1 4 6 4 1
```

In the above algorithm, we are taking an integer input num from the user to print the num number of Pascal Triangle rows.

1. The pascalTriangle() function is called with the num parameter. Consider the num = 5. Note that the number of rows and columns of the triangle are equal to num.

2. The first for loop in pascalTriangle() iterates through each row(from 0 to num). That is "n" from the formula nCk

3. The second for loop in the pascalTriangle() iterates through each column(from 0 to num+1, since each row has elements equal to row number), that is, each element of the current row, "k" from the formula nCk​

4.In the second for loop, to print each element of the current row, we are passing the current row number n and column number k to factFormula() function.

5. In factFormula(), we have built the nCk formula. 

6. To find the factorials of the respective numbers in the formula, we have built another function findFact() which returns the calculated factorial of the given number.

7. From the factFormula(), we call the findFact() function which returns the factorial of the number passed as the parameter according to the ​nCk formula.

8.  factFormula() returns the calculated value to the for loop and the value gets printed.

9. We have written an empty print() statement at the end of the second for loop for a new line after each row.

<h3>Second approach:</h3>

Approach 2: O(n**2) time and O(n**2)
 extra space
Look at the image of the Pascal Triangle again. Did you notice something? Let me tell you, the value at each position of the Pascal Triangle is the direct sum of the above two values. What does this mean? To get a clear idea, have a look at the image below:

In the above image, the pointed values are calculated by the sum of the two values above it. Also, look at the matrix representation of the Pascal Triangle for understanding the below algorithm better.


​Hersfold on the English Wikipedia, Public domain, via Wikimedia Commons​

Also note that, in this algorithm, we are constantly requiring values of the previous now. Therefore, we will create a 2D array to store the values for accessing them later.

We are using a formula to calculate the sum of the above two values:

Here, n = current row, k = current column.

arr[n][k] = arr[n - 1][k - 1] + arr[n - 1][k]

For example,

arr[3][2] = arr[3-1][2-1] + arr[3-1][2] 

             = arr[2][1] + arr[2][2] 

             = 2 + 1 = 3

Let's see the algorithm:
```
Python
def pascalTriangle(num:int):

	# 2D array to store the values
	matrix = [[0 for x in range(num)]
			for y in range(num)]

	# iterating through the rows
	for n in range (0, num):

		# iterating through each value of the row
		for k in range (0, n + 1):

			# first and last column are 0
			if(k == 0 or k == n):
				matrix[n][k] = 1
				print(matrix[n][k], end = " ")

			# calculating the sum of the above two values
			else:
				matrix[n][k] = (matrix[n - 1][k - 1] +
								matrix[n - 1][k])
				print(matrix[n][k], end = " ")
		print("\n", end = "")

# Driver Code
num = int(input("Enter the number of rows: "))
pascalTriangle(num)
​Enter the number of rows: 4 

1 

1 1

1 2 1

1 3 3 1
```
In the above algorithm, we are taking an integer input num from the user to print the num number of Pascal Triangle rows.

1. The pascalTriangle() function is called with the num parameter. Consider the num = 4. Note that the number of rows and columns are equal to num. 

2. Here, we are creating an array matrix of size num*num to store the values for accessing later for calculating the sum.

3. The first for loop in pascalTriangle() iterates through each row(from 0 to num).  

4. The second for loop in the pascalTriangle() iterates through each column(from 0 to num +1, since each row has elements equal to row number).

5. Note that in each row, the first and the last column is 1. Therefore, in the second for loop we use the if condition to check whether its 0(first column) or num(last column)------Since the last column number is equal to the current row number

6. If the column is neither first or last, the control goes to the else condition where the value is calculated using the formula discussed above the algorithm. That is,

arr[n][k] = arr[n - 1][k - 1] + arr[n - 1][k]

7. Note that while printing the values, we are simultaneously storing them in the array matrix.

Let's see the third approach:

Approach 3: 
O(n**2) time and O(1)
 extra space
This is the most optical approach compared to the above two algorithms. This approach is found by a little modification in the first approach. The time complexity in the first approach was 
O(n**2)

resulting in the worst time complexity. We can use the same nCk formula, but, in a smarter way. Look at the image below and understand the pattern between the consecutive values of each row. Let's consider the third row:


So, from the above pattern we can come up with a formula:

Here, n = current row, k = current column

C(n,k)=C(n,k−1)∗(n−k+1)k
Explanation: From the above formula and the pattern in the image,

C(n, k-1) refers to the previous value of the current row we use, to get the current value (marked in blue)

(n - k + 1) refers to the part marked in green

k indicates that divide with the current column number(marked in red)

For example:

3C2=C(3,1)∗(3−2+1)2      =3∗22      =3
 

Let's see the algorithm:

```
Python
def pascalTriangle(num):  
  
    for n in range(1, num + 1):  
        C = 1   
        for k in range(1, n + 1):  
              
            # value of first column is always 1  
            print(C, end = " ")  
            C = int(C * (n - k) / k)  
        print("")  
```  
```
# Driver code  
num = int(input("Enter the number of rows: "))
pascalTriangle(num)<br/>
​Enter the number of rows: 5 

1 

1 1

1 2 1

1 3 3 1 

1 4 6 4 1
```
In the above algorithm, we are taking an integer input num from the user to print the num number of Pascal Triangle rows. 

1. The pascalTriangle() function is called with the num parameter. 

2. The first for loop in pascalTriangle() iterates through each row. Note that here we are starting the for loop from index value 1 since starting from index value 0 will give a ZeroDivisionError while dividing in the formula ahead.

3. The second for loop in the pascalTriangle() iterates through each value in the row(each column).

4.Here, we are using a variable C for storing the previous value so that we can use this value for calculating the consecutive values of the current row.

5. We are initializing the variable C with 1, C = 1, as the first element of each row is always 1. The value of C keeps changing as we move forward in the current row and again initialized to 1 when a new row starts(at the start of second for loop).

6. We are using the formula discussed above to store the new consecutive values in variable C.

7. Note that since we are starting both the for loops from index value 1, the formula becomes: C * (n - k) / k   instead of  C * (n - k+1) / k 