# Module-9-survivor-
#Objectives
#Compare three visualization systems in R: base graphics, lattice, and ggplot2.
#Apply each system to the same dataset and observe similarities and differences.
#Develop clear, reproducible code and articulate your insights.
#Choose one dataset from the Rdatasets collectionLinks to an external site.. 
#Load it in R with:

#install.packages("alone")
  
getwd()

# Read the CSV file
survivor <- read.csv("Survivalists.csv")

# Preview it
head(survivor)

#Tasks
#Base R Graphics
#Create at least two plots using base R functions. Examples:

str(survivor)
names(survivor)
  
# Scatter plot
plot(survivor$age, survivor$days_lasted,
    main   = "Base R: age vs. days_lasted",
    xlab   = "age",
    ylab   = "days_lasted",
     pch = 19,
     col = "blue")

# Histogram
hist(survivor$age,
    main  = "Base R: Distribution of age",
    xlab  = "age",
    col = "darkgreen")

#Lattice Graphics
#Use the lattice package to produce conditioned or multivariate plots. Examples:

library(lattice)

# Conditional scatter plot (small multiples)
xyplot(days_lasted ~ age | gender,
       data = survivor,
       main = "Lattice: days_survived vs. age by gender",
       col = "darkblue")

# Box-and-whisker plot
bwplot(days_lasted ~ gender,
       data = survivor,
       main = "Lattice: days_lasted by gender")

#ggplot2
#Use ggplot2’s grammar of graphics to create layered visuals. Examples:
  library(ggplot2)

# Scatter plot with smoothing
ggplot(survivor, aes(x = age, y = days_lasted, color = gender)) +
  geom_point(size = 3, alpha = 0.7) +
  geom_smooth(method = "lm") +
  labs(title = "ggplot2: days_lasted vs. age with trend by gender")

# Faceted histogram
ggplot(survivor, aes(age)) +
  geom_histogram(binwidth = 1) +
  facet_wrap(~ gender) +
  labs(title = "ggplot2: age distribution by gender")

