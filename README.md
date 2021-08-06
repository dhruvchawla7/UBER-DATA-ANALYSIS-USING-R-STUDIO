# UBER-DATAANALYSIS-USING-R-STUDIO
The project titled 'Uber Data Analysis Project' emphasizes on data visualization techniques and the various ways to visualize data according to the requirements.

INTRO

Data visualization is the graphical representation of information and data. With the help of visualization, it becomes feasible to gain the benefit of understanding 
the complex data and insights that would help individuals to craft decisions. Here, we have made use of R as our programming language and Rstudio as a platform for 
implementing the data visualization process. The libraries being used in this project are ggplot, ggthemes, lubridate and many others. 
The project uses the new york city Uber dataset for months april, may, june, july, august to analyze the uber pickups and trips in new york city.
The main objective of this project is to comprehend the complexity of data and make it easier to understand the meaning of data by refining it into smaller grains and
visualizing it.

LIBRARIES USED
R Libraries used in project

(A)library(ggplot2)

ggplot2 is an open-source data visualization package for the statistical programming
language R. Created by Hadley Wickham in 2005, ggplot2 is an implementation of
Leland Wilkinson's Grammar of Graphics—a general scheme for data visualization
which breaks up graphs into semantic components such as scales and layers. ggplot2
can serve as a replacement for the base graphics in R and contains a number of defaults
for web and print display of common scales. Since 2005, ggplot2 has grown in use to
become one of the most popular R packages.
ggplot2 package
ggplot2 is a powerful and flexible R package, implemented by Hadley Wickham, for
producing elegant graphics.
The concept behind ggplot2 divides plot into three different fundamental parts: Plot =
data + Aesthetics + Geometry.
The principal components of every plot can be defined as follow:
● data is a data frame
● Aesthetics is used to indicate x and y variables. It can also be used to
control the color, the size or the shape of points, the height of bars, etc…..
● Geometry defines the type of graphics (histogram, box plot, line plot,
density plot, dot plot, ….)
install.packages("ggplot2")
library(ggplot2)
There are two major functions in the ggplot2 package: qplot() and ggplot() functions.
● qplot() stands for quick plot, which can be used to easily produce simple
plots.
● ggplot() function is more flexible and robust than qplot for building a plot
piece by piece
While qplot() is useful to plot quickly, most of time, one should use ggplot() for
systemic plotting
qplot(x, y, dataframe, geom="type")
ggplot(data, aes(x,y))+ geom_type() + options
x<-1:30
y<-c(5,4,5,3,4,6,7,4,2,1,5,6,2,2,2,
5,6,7,8,6,2,8,7,8,8,3,3,7,2,1)
z<-c('A','B','A','A','B','A','B','B','A','A',
'B','A','A','A','B','A','A','B','A','B',
'B','A','A','A','B','A','A','B','A','B')
df<-data.frame(x,y,z)

(B) library(ggthemes)

ggthemes is an open source data visualization library that has quick functions to
change plot themes and to customize the appearance of the plot background. Using
ggthemes, we can:
o Change the colors of the plot panel background and the grid lines
o Remove plot panel borders and grid lines
o Change the plot background color (not the panel)
Use a custom theme
o theme_tufte : a minimalist theme
o theme_economist : theme based on the plots in the economist magazine
o theme_stata: theme based on Stata graph schemes.
o theme_wsj: theme based on plots in the Wall Street Journal
o theme_calc : theme based on LibreOffice Calc
o theme_hc : theme based on Highcharts JS
o Functions: theme(), theme_bw(), theme_grey(), theme_update(),
theme_blank(), theme_classic(), theme_minimal(), theme_void(), theme_dark(),
element_blank(), element_line(), element_rect(), element_text(), rel()
Example of plot
library(ggplot2)
p <- ggplot(ToothGrowth, aes(x=dose, y=len)) + geom_boxplot()
P
Quick functions to change plot themes
Several functions are available in ggplot2 package for changing quickly the theme of
plots:
· theme_gray : gray background color and white grid lines
· theme_bw : white background and gray grid lines
p + theme_gray(base_size = 14)
p + theme_bw()
· theme_linedraw : black lines around the plot
· theme_light : light gray lines and axis (more attention towards the
data)
p + theme_linedraw()
p + theme_light()
· theme_minimal: no background annotations
· theme_classic : theme with axis lines and no grid lines
p + theme_minimal()
p + theme_classic()
· theme_void: Empty theme, useful for plots with non-standard
coordinates or for drawings
· theme_dark(): Dark background designed to make colours pop out
p + theme_void()
p + theme_dark()

The functions theme_xx() can take the two arguments below :
· base_size : base font size (to change the size of all plot text elements)
· base_family : base font family
The size of all the plot text elements can be easily changed at once :
# Example 1
theme_set(theme_gray(base_size = 20))
ggplot(ToothGrowth, aes(x=dose, y=len)) + geom_boxplot()
# Example 2
ggplot(ToothGrowth, aes(x=dose, y=len)) + geom_boxplot()+
theme_classic(base_size = 25)

(C) library(lubridate)

Lubridate is an R package that makes it easier to work with dates and times. Below is
a concise tour of some of the things lubridate can do for you. Lubridate was created
by Garrett Grolemund and Hadley Wickham, and is now maintained by Vitalie Spinu.
Parsing dates and times
Getting R to agree that your data contains the dates and times you think it does can be
tricky. Lubridate simplifies that. Identify the order in which the year, month, and day
appears in your dates. Now arrange "y", "m", and "d" in the same order. This is the
name of the function in lubridate that will parse your dates. For example,
library(lubridate)
#>
#> Attaching package: 'lubridate'
#> The following objects are masked from 'package:base':
14
#>
#> date, intersect, setdiff, union
ymd("20110604")
#> [1] "2011-06-04"
mdy("06-04-2011")
#> [1] "2011-06-04"
dmy("04/06/2011")
#> [1] "2011-06-04"
Lubridate's parse functions handle a wide variety of formats and separators, which
simplifies the parsing process.
If your date includes time information, add h, m, and/or s to the name of the function.
ymd_hms is probably the most common date time format. To read the dates in a certain
time zone, supply the official name of that time zone in the tz argument.
arrive <- ymd_hms("2011-06-04 12:00:00", tz = "Pacific/Auckland")
arrive
#> [1] "2011-06-04 12:00:00 NZST"
leave <- ymd_hms("2011-08-10 14:00:00", tz = "Pacific/Auckland")
leave
#> [1] "2011-08-10 14:00:00 NZST"
Setting and Extracting information
Extract information from date times with the functions second, minute, hour, day,
wday, yday, week, month, year, and tz. You can also use each of these to set (i.e,
change) the given information. Notice that this will alter the date time. wday and month
have an optional label argument, which replaces their numeric output with the name
of the weekday or month.
second(arrive)
#> [1] 0
second(arrive) <- 25
arrive
#> [1] "2011-06-04 12:00:25 NZST"
second(arrive) <- 0
wday(arrive)
#> [1] 7
wday(arrive, label = TRUE)
#> [1] Sat
#> Levels: Sun < Mon < Tue < Wed < Thu < Fri < Sat

(D) library(dplyr)

The dplyr package in R is a structure of data manipulation that provides a uniform set
of verbs, helping to resolve the most frequent data manipulation hurdles.
The dplyr package performs the steps given below quicker and in an easier fashion:
o By limiting the choices the focus can now be more on data manipulation difficulties.
o There are uncomplicated “verbs”, functions present for tackling every common data
manipulation and the thoughts can be translated into code faster.
o There are valuable backends and hence waiting time for the computer reduces.
Important Verb Functions
dplyr package provides various important functions that can be used for Data
Manipulation. These are:
o filter() Function: For choosing cases and using their values as a base for it.
o arrange(): For reordering of the cases.
o select() and rename(): For choosing variables and using their names as a base for
doing so.
o mutate() and transmute(): Addition of new variables which are the functions of
prevailing variables.
o summarise(): Condensing various values to one value.
o sample_n() and sample_frac(): For taking random specimens.

(E) library(tidyr)

tidyr is a new package that makes it easy to “tidy” your data. Tidy data is data that’s
easy to work with: it’s easy to munge (with dplyr), visualise (with ggplot2 or ggvis)
and model (with R’s hundreds of modelling packages). The two most important
properties of tidy data are:
o Each column is a variable.
o Each row is an observation.
Arranging your data in this way makes it easier to work with because you have a
consistent way of referring to variables (as column names) and observations (as row
indices). When using tidy data and tidy tools, you spend less time worrying about how
to feed the output from one function into the input of another, and more time answering
your questions about the data.
To tidy messy data, you first identify the variables in your dataset, then use the tools
provided by tidyr to move them into columns. tidyr provides three main functions for
tidying your messy data: gather(), separate() and spread().
gather() takes multiple columns, and gathers them into key-value pairs: it makes
“wide” data longer. Other names for gather include melt (reshape2), pivot
(spreadsheets) and fold (databases).

(F) library(DT)

The R package DT provides an R interface to the JavaScript library DataTables. R
data objects (matrices or data frames) can be displayed as tables on HTML pages, and
DataTables provides filtering, pagination, sorting, and many other features in the
tables.
The main function in this package is datatable(). It creates an HTML widget to display
R data objects with DataTables.

(G) library(scales)

One of the most difficult parts of any graphics package is scaling, converting from
data values to perceptual properties. The inverse of scaling, making guides (legends
and axes) that can be used to read the graph, is often even harder! The idea of the scales
package is to implement scales in a graphics system agnostic, so that everyone can
benefit by pooling knowledge and resources about this tricky topic.

The scales package is made up of the following interdependent components
o Palettes: pal for short, describe the useful palettes of aesthetics.
o Transformations: trans for short, describe common scale transformations, their
inverses, and ways of generating breaks and labels.
o Bounds: various ways of rescaling the data
o Scaling functions: pull together palettes, bounding functions and transformations
to provide a complete pathway from raw data to perceptual properties
o Mutable ranges: in many graphics pathways, scale ranges can not be computed in
a single pass, but must be computed over multiple groups or multiple panels. The
mutable ranges (implemented with R's new reference based class) provide a thin layer
of mutability to make this task easier.


