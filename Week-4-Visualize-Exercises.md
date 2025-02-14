# Visualize Data
Rachel Ramos

## Your Turn 0

Add a setup chunk that loads the tidyverse packages.

``` r
head(mpg)
```

    # A tibble: 6 × 11
      manufacturer model displ  year   cyl trans      drv     cty   hwy fl    class 
      <chr>        <chr> <dbl> <int> <int> <chr>      <chr> <int> <int> <chr> <chr> 
    1 audi         a4      1.8  1999     4 auto(l5)   f        18    29 p     compa…
    2 audi         a4      1.8  1999     4 manual(m5) f        21    29 p     compa…
    3 audi         a4      2    2008     4 manual(m6) f        20    31 p     compa…
    4 audi         a4      2    2008     4 auto(av)   f        21    30 p     compa…
    5 audi         a4      2.8  1999     6 auto(l5)   f        16    26 p     compa…
    6 audi         a4      2.8  1999     6 manual(m5) f        18    26 p     compa…

## Your Turn 1

Run the code on the slide to make a graph. Pay strict attention to
spelling, capitalization, and parentheses!

``` r
ggplot(mpg) + #can add just the data set.. initializing plot with ggplot.. plus always at the end 
  geom_point(aes(x=displ, y = hwy)) #mapping aesthetics then labels x and y axis.. adding layers
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/mpg_map_scatter-1.png)

## Your Turn 2

Replace this scatterplot with one that draws boxplots. Use the
cheatsheet. Try your best guess.

``` r
ggplot(data = mpg) +
  geom_boxplot(mapping = aes(x = class, y = hwy))
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/Boxplot-1.png)

## Your Turn 3

Make a histogram of the `hwy` variable from `mpg`. Hint: do not supply a
y variable.

``` r
ggplot(data=mpg) + 
  geom_histogram(mapping=aes(x=hwy))
```

    `stat_bin()` using `bins = 30`. Pick better value with `binwidth`.

![](Week-4-Visualize-Exercises_files/figure-commonmark/histogram-1.png)

## Your Turn 4

Use the help page for `geom_histogram` to make the bins 2 units wide.

``` r
ggplot(data=mpg) + 
  geom_histogram(mapping=aes(x=hwy) , binwidth = 2)
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/histogram%20binwidth%20mod-1.png)

## Your Turn 5

Add `color`, `size`, `alpha`, and `shape` aesthetics to your graph.
Experiment.

``` r
ggplot(data=mpg) + 
  geom_point(mapping=aes(x=displ,
                         y=hwy,
                         color=class))+
  labs( x="Engine Size Displacemnet",
        y= " Highway Mileage",
        color= "Class of Vehicle",
        title= "The Bigger the Engine the Less Mileage We Get on the Highway")+ 
  theme_light()
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/Scatterplot%20for%20mileage-1.png)

``` r
                         #shape=class
                         #alpha=class
                         #size = class
```

## Help Me

What do `facet_grid()` and `facet_wrap()` do? (run the code, interpret,
convince your group)

``` r
# Makes a plot that the commands below will modify
q <- ggplot(mpg) + geom_point(aes(x = displ, y = hwy))

q + facet_grid(. ~ cyl) #creates colomns(4), 1 row
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/Mulitple%20plots-1.png)

``` r
q + facet_grid(drv ~ .) #creates rows (4), 1 col
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/Mulitple%20plots-2.png)

``` r
q + facet_grid(drv ~ cyl) #creates rows and columns 4&4
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/Mulitple%20plots-3.png)

``` r
q + facet_wrap(~ class) #creates rows and columns for each class
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/Mulitple%20plots-4.png)

## Your Turn 6

Make a bar chart `class` colored by `class`. Use the help page for
`geom_bar` to choose a “color” aesthetic for class.

``` r
ggplot(data=mpg) + 
  geom_bar(mapping = aes(x=class, fill= class)) + guides(fill= "none") + 
  labs(x=" Class of Vehicle",
       y= "Nuber of Vehicles in Sample")
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-9-1.png)

``` r
#ggplot(data=mpg) + 
 # geom_bar(mapping = aes(x=class, fill= class)) + guides(fill= "none") + 
 # labs(x=" Class of Vehicle",
       #y= "Nuber of Vehicles in Sample",
      # theme_bw()
```

``` r
ggplot(data=mpg) + 
  geom_bar(mapping = aes(x=class, fill= drv), 
           position=position_dodge())+ 
  labs(x=" Class of Vehicle",
       y= "Nuber of Vehicles in Sample",
       fill= "Type of drive" )
```

![](Week-4-Visualize-Exercises_files/figure-commonmark/unnamed-chunk-10-1.png)

## Quiz

What will this code do?

``` r
ggplot( mpg, aes( x=displ, y=hwy))+ 
  geom_point(aes(color=class))+
  geom_smooth(color="black",
              se=FALSE,
              method="lm")+
  scale_color_viridis_d()
```

    `geom_smooth()` using formula = 'y ~ x'

![](Week-4-Visualize-Exercises_files/figure-commonmark/Combined%20scatter-1.png)

``` r
  ggsave("my-plot.jpg", width =6, height=4)
```

    `geom_smooth()` using formula = 'y ~ x'

``` r
  #code will add new layers
```

------------------------------------------------------------------------

# Take aways

You can use this code template to make thousands of graphs with
**ggplot2**.

``` r
ggplot(data = <DATA>) +
  <GEOM_FUNCTION>(mapping = aes(<MAPPINGS>))
```
