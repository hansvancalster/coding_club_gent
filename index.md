# Tutorial name
## Author

### Tutorial Aims

#### <a href="#section1"> 1. Import data in R</a>

#### <a href="#section2"> 2. Create a plot</a>

#### <a href="#section3"> 3. Save the plot</a>

### You can get all of the resources for this tutorial from <a href="https://github.com/ourcodingclub/CC-EAB-tut-ideas" target="_blank">this GitHub repository</a>. Clone and download the repo as a zip file, then unzip it.

<a name="section1"></a>



## 1. Import data in R

```{r}
load("traits.RData")
load("traits_sum.RData")


```

Open `RStudio`, create a new script by clicking on `File/ New File/ R Script` set the working directory and load the packages we'll need.

```r
# Set the working directory
setwd("your_filepath")

# Load packages
library(ggplot2)
library(dplyr)
# Load libraries
library(corrplot)
library(ggplot2)



```

<a name="section2"></a>

## 2. Create a plot

You can add more text and code, e.g.

```r
# Add your code and comments here
# Comparing within-individual correlations
# Trait-trait correlation plot
(correlation <- corrplot(cor(traits[,2:5], use = "pairwise.complete.obs")))

# Save the plot in your working directory
png(filename = "trait_correlation.png", width = 600, height = 600)
(correlation <- corrplot(cor(data[,2:6], use = "pairwise.complete.obs")))
dev.off()

# Graph raw trait data behind mean +/- 95% CI's and save the file
(trait.plot <- ggplot()+
    geom_point(data = dlong, mapping = aes(x = SpeciesName, y = value, colour = Trait), alpha = 0.1) +
    geom_errorbar(data = dsumm, mapping = aes(x = SpeciesName, ymin = q2.5, ymax = q97.5, group = Trait), width = 0.3) +
    geom_point(data = dsumm, mapping = aes(x = SpeciesName, y = mean, group = Trait), size = 4, colour = "black") +
    geom_point(data = dsumm, mapping = aes(x = SpeciesName, y = mean, colour = Trait), size = 3) +
    facet_wrap(~Trait, scales = "free_y")+
    theme_classic() +
    scale_x_discrete(labels = c("Dryas", "Eriophorum", "Oxyria", "Salix")) +
    ylab("Trait Value") +
    xlab("Species"))

# We can save plots made using ggplot2 with ggsave, which is just one line of code
ggsave(trait.plot, filename = "traits.png", height = 5, width = 10)

```

<a name="section3"></a>

## 3. The third section

Here you can add some more text if you wish.

```r
# Add more code and comments
```

At this point it would be a good idea to include an image of what the plot is meant to look like so people can check they've done it right. Replace `IMAGE_NAME.png` with your own image file:

<center> <img src="{{ site.baseurl }}/IMAGE_NAME.png" alt="Img" style="width: 800px;"/> </center>

This is the end of the tutorial. Here is a summary of what we learned:

##### - something
##### - something else
##### - and a third thing

We can also provide some useful links:

For more on `ggplot2`, read the official <a href="https://www.rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf" target="_blank">ggplot2 cheatsheet</a>.
