#Working With Data

##Load required packages from the library:
* library(dplyr) - as with "tidyr", "ggplot2"
* I've created a variable called path2csv, which contains the full file path to the dataset. Call read.csv() with two arguments, path2csv and stringsAsFactors = FALSE, and save the result in a new variable called mydf. Check ?read.csv
* Use dim() to look at the dimensions of mydf.



#Step-by-step:
* The first step of working with data in dplyr is to load the data into what the package authors call a 'data frame tbl'
or 'tbl_df'. Use the following code to create a new tbl_df called cran:
* To avoid confusion and keep things running smoothly, let's remove the original data frame from your workspace with rm("mydf").
* From ?tbl_df, "The main advantage to using a tbl_df over a regular data frame is the printing." Let's see what is meant by this. Type cran to print our tbl_df to the console.
* According to the "Introduction to dplyr" vignette written by the package authors, "The dplyr philosophy is to have small functions that each do one thing well." Specifically, dplyr supplies five 'verbs' that cover most fundamental data manipulation tasks: select(), filter(), arrange(), mutate(), and summarize().
* The first thing to notice is that we don't have to type cran$ip_id, cran$package, and cran$country, as we normally would when referring to columns of a data frame. The select() function knows we are referring to columns of the cran dataset.
* Also, note that the columns are returned to us in the order we specified, even though ip_id is the rightmost column in the original dataset.
* Recall that in R, the `:` operator provides a compact notation for creating a sequence of numbers. For example, try 5:20.
* Normally, this notation is reserved for numbers, but select() allows you to specify a sequence of columns this way, which can save a bunch of typing. Use select(cran,  r_arch:country) to select all columns starting from r_arch and ending with country.
* We can also select the same columns in reverse order. Give it a try.
* Instead of specifying the columns we want to keep, we can also specify the columns we want to throw away. To see how this works, do select(cran, -time) to omit the time column.
* Now that you know how to select a subset of columns using select(), a natural next question is "How do I select a subset of rows?" That's where the filter() function comes in.
* Use filter(cran, package == "swirl") to select all rows for which the package variable is equal to "swirl". Be sure to use two equals signs side-by-side!
* You can specify as many conditions as you want, separated by commas. For example filter(cran, r_version == "3.1.1", country == "US") will return all rows of cran corresponding to downloads from users in the US running R version 3.1.1.
* Sometimes we want to order the rows of a dataset according to the values of a particular variable. This is the job of arrange().
* Now, to order the ROWS of cran2 so that ip_id is in ascending order (from small to large), type arrange(cran2, ip_id)
* To do the same, but in descending order, change the second argument to desc(ip_id), where desc() stands for 'descending'.
* We can also arrange the data according to the values of multiple variables. For example, arrange(cran2, package, ip_id) will first arrange by package names (ascending alphabetically), then by ip_id. This means that if there are multiple rows with the same value for package, they will be sorted by ip_id (ascending numerically).
* To illustrate the next major function in dplyr, let's take another subset of our original data. Use **select()** to grab 3 columns from cran -- ip_id,
 package, and size (in that order) -- and store the result in a new variable called cran3
* It's common to create a new variable based on the value of one or more variables already in a dataset. The **mutate()** function does exactly this.
* We want to add a column called size_mb that contains the download size in megabytes. Here's the code to do it: mutate(cran3, size_mb = size / 2^20)
* One very nice feature of **mutate()** is that you can use the value computed for your second column (size_mb) to create a third column, all in the same line of code. To see this in action, repeat the exact same command as above, except add a third argument creating a column that is named size_gb and equal to size_mb / 2^10.
* The last of the five core dplyr verbs, **summarize()**, collapses the dataset to a single row. Let's say we're interested in knowing the average download size. summarize(cran, avg_bytes = mean(size)) will yield the mean value of the size variable. Here we've chosen to label the result 'avg_bytes', but we could have named it anything
* That's not particularly interesting. **Summarize()** is most useful when working with data that has been grouped by the values of a particular variable.
*