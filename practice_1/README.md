[![Typing SVG](https://readme-typing-svg.herokuapp.com?color=%2336BCF7&lines=RStudio+Practice1)](https://git.io/typing-svg)
## Медведев Александр БИСО-02-20

```R
install.packages("swirl")
library("swirl")
swirl()
```
![image](https://github.com/zxcenigma/R_practice/assets/90748931/692ed0bb-866d-46e6-b3e0-1f76b5ab256b)

### 1. Basic Building Blocks

In its simplest form, R can be used as an interactive calculator. Type 5 + 7 and press Enter.

```R
5 + 7
[1] 12
```
To assign the result of 5 + 7 to a new variable called x, you type x <- 5 + 7. This can be read
as 'x gets 5 plus 7'. Give it a try now.

```R
x <- 5 + 7
```
To view the contents of the variable x, just type x and press Enter. Try it now.

```R
x
[1] 12
```

Now, store the result of x - 3 in a new variable called y.

```R
y <- x - 3
```

What is the value of y? Type y to find out.

```R
> y
[1] 9
```
The easiest way to create a vector is with the c() function, which stands for ‘concatenate’ | or ‘combine’. To create a vector containing the numbers 1.1, 9, and 3.14, type c(1.1, 9, | 3.14). Try it now and store the result in a variable called z.

```R
z <- c(1.1, 9, 3.14)
```

Anytime you have questions about a particular function, you can access R’s built-in help | files via the ? command. For example, if you want more information on the c() function, | type ?c without the parentheses that normally follow a function name. Give it a try.

```R
?c
```

Great job!

  |====================================                                                      |  39%
| Type z to view its contents. Notice that there are no commas separating the values in the output.

```R
z
[1] 1.10 9.00 3.14

```
All that hard work is paying off!

  |======================================                                                    |  42%
| You can combine vectors to make a new vector. Create a new vector that contains z, 555, then z
| again in that order. Don't assign this vector to a new variable, so that we can just see the
| result immediately.

```R
c(z, 555, z)
[1]   1.10   9.00   3.14 555.00   1.10   9.00   3.14
```

| You are doing so well!

  |========================================                                                  |  45%
| Numeric vectors can be used in arithmetic expressions. Type the following to see what happens: z
| * 2 + 100.

```R
z * 2 + 100
[1] 102.20 118.00 106.28
```

Take the square root of z - 1 and assign it to a new variable called my_sqrt.

```R
my_sqrt <- sqrt(z - 1)
```

Before we view the contents of the my_sqrt variable, what do you think it contains?
#
1: a vector of length 0 (i.e. an empty vector)   
2: a single number (i.e a vector of length 1)   
3: a vector of length 3   
                    Выбор:2 																																																								   
										
Think about how R handled the other 'vectorized' operations: element-by-element.  
#
1: a vector of length 3
2: a single number (i.e a vector of length 1)
3: a vector of length 0 (i.e. an empty vector)                        
			Выбор:1
