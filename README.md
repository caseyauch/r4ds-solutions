# r4ds-solutions

# 3.2.1
### Run `ggplot(data = mpg)` what do you see?
An empty gray plot. 
```{r}
ggplot(data = mpg)
```

### How many rows are in mpg? How many columns?
234 rows, 11 columns

### What does the `drv` variable describe?  Read the help for `?mpg` to find out.
```{r}
?mpg
```
`drv` is the type of drive train, where f = front-wheel drive, r = rear wheel drive, 4 = 4wd

### Make a scatterplot of `hwy` vs `cyl`.
```{r}
ggplot(mpg) + geom_point(mapping = aes(x=cyl, y=hwy))
```

### What happens if you make a scatterplot of `class` vs `drv`. Why is the plot not useful?
```{r}
ggplot(mpg, aes(x=class, y=drv)) + geom_point()
```
This plot isn’t useful because the two variables (`class` and `drv`) tell you nothing about fuel efficiency. You’ve got to use `cty` or `hwy`. EDIT: they're both categorical variables.  

# 3.3.1
### What's gone wrong with this code? Why are the points not blue?
To set aesthetic manually, it must be outside of aes(). 
```{r}
ggplot(data = mpg) + 
  geom_point(mapping = aes(x = displ, y = hwy), color = "blue")
```

### Which variables in `mpg` are categorical? Which variables are continuous? 
Categorical: fl, class, cyl, trans, drv, manufacturer, model, year
Continuous: cty, hwy

### Map a continuous variable to `color`, `size`, and `shape`. How do these aesthetics behave differently for categorical vs. continuous variables? 
For continuous variables, `color` is a gradient of blue. A continuous variable can’t be mapped to `shape`. `size` should only be used for discrete variables. 

### What happens if you map the same variable across multiple aesthetics? What happens if you map different variables across multiple aesthetics?
There's lots of uniformality. You can't map different varaibles across the same aesthetic. 

### What does the `stroke` aesthetic do? What shapes does it work with?
The stroke is the border of a shape. It works well with squares and circles, not plus signs or triangles. 
```{r}
ggplot(data = mpg) + geom_point(aes(x = cty, y = hwy, stroke = displ), shape = 21)
```

### What happens if you set an aesthetic to something other than a variable name, like `displ < 5`?
Setting an aesthetic to an argument like `year < 2000` evaluates the argument for every point (true/false). 
```{r}
ggplot(data = mpg) + geom_point(aes(x = cty, y = hwy, colour = year < 2000))
```

# 3.5.1
### What happens if you facet on a continuous variable?
There are many plots, too many to be helpful, because you get a row/column for each unique variable.

### What do the empty cells in plot with `facet_grid(drv ~ cyl)` mean?
Empty cells are a result of no value matching those rows. For this example, there are no car in the data set wih 5 `cyl` and `4` wheel drive.

### What plots does the following code make? What does `.` do?
`.` is just a placeholder and does nothing. 
