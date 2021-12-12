Advent of Code 2021: Day 8
================

## **— Day 8: Seven Segment Search —**

``` r
library(tidyverse)

input <- read_delim("inputs/day8_input.txt", col_names = FALSE, delim = "\n") %>% 
                separate(X1, into = c("inputs", "outputs"), sep = " \\| ") %>% 
                extract(outputs, into = c("one", "two", "three", "four"), 
                        regex = "([a-z]+) ([a-z]+) ([a-z]+) ([a-z]+)")

input %>% 
        select(-inputs) %>% 
        mutate(across(.fns = str_length)) %>% 
        pivot_longer(everything()) %>% 
        filter(value %in% c(2, 3, 4, 7)) %>% 
        nrow()
```

    ## [1] 369
