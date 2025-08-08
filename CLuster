#Load necessary libraries 
install.packages("readr")
install.packages("dplyr")
install.packages("factoextra")
install.packages("ggplot2")
library(readr)
library(dplyr)
library(factoextra)
library(ggplot2)

#Load the data
data <- read.csv('/Users/quanquan/Downloads/transactions.csv', header = T ) 
data <- read_delim('/Users/quanquan/Downloads/transactions.csv', delim=';',escape_double = FALSE, trim_ws = TRUE)
data = as.data.frame(data)

#Check the first lines of the data
head(data,10)

#Show basic information about the data structure
str(data)

#Data summary
summary(data)

#Bar chart for the quantity of products sold by product
library(ggplot2)
ggplot(data, aes(x = product, fill = product)) +
  geom_bar(stat = "count") +  #  stat="count" to count
  ggtitle("Number of products sold by product") +
  xlab("Product") +
  ylab("Quantity") 

#Frequency table of orders by month
#Change 'orderdate' to Date format
data$orderdate <- as.Date(data$orderdate,
                                  format="%d/%m/%Y")
#Create a new column 'month' to store month and year information
data$month <- format(data$orderdate,"%Y-%m")
ggplot(data, aes(x = month)) +
  geom_bar(stat = "count", fill = "skyblue", color = "black") +
  ggtitle("Order frequency by month") +
  xlab("Month") +
  ylab("Frequency")

#Create a frequency table combining gender and product
freq_table <- table(data$gender, data$product)
#Install package reshape2
install.packages("reshape2")
library(reshape2)
#Heatmap
ggplot(melt(freq_table), aes(x = Var1, y = Var2, fill = value)) +
  geom_tile() +
  scale_fill_gradient(low = "white", high = "red") +
  ggtitle("Heatmap of gender and products") +
  xlab("Gender") +
  ylab("Product")

#Convert gender column to numeric form: male =1, female=0
data$gender <- ifelse(data$gender == "male",1, 0)
#Convert the product column to numeric form with
#a=1, b=2, c=3, d=4, e=5, f=6, g=7, h=8, i=9
data$product <- as.numeric(factor(data$product))

#Remove unnecessary columns such as clientId, orderId, orderdate 
data=data[,-c(1,2,5,8)]

#Re-check the data after removing NA rows
head(data)
data <- na.omit(data)

#Data scaling
data_scale= scale(data)
#Implementation
fviz_nbclust(data_scale, kmeans, method="wss")
fviz_nbclust(data_scale, kmeans, method="gap_stat") 
fviz_nbclust(data_scale, kmeans, method="silhouette")

#Set seed
set.seed(123)
km <- kmeans(data_scale,3)
km
#Add the cluster label to the data
dd=data
dd$label<-km$cluster
head(dd)
tail(dd)

#Final result
fviz_cluster(km, data = data,
             palette= c('red', 'blue', 'yellow' ),
             ellipse.type= 'euclid')
# Filter Cluster1 
label1_dd<- dd %>% filter(label == 1)
# Summary of categorical variables (gender and product)
gender_summary1 <- label1_dd %>%
  group_by(gender) %>%
  summarise(count = n())

product_summary1 <- label1_dd %>%
  group_by(product) %>%
  summarise(count = n())
# Summary of numerical variables (Quantity and Price)
numeric_summary1 <- label1_dd %>%
  summarise(
    mean_quantity = mean(Quantity, na.rm = TRUE),
    sd_quantity = sd(Quantity, na.rm = TRUE),
    mean_price = mean(Price, na.rm = TRUE),
    sd_price = sd(Price, na.rm = TRUE)
  )
# Print summaries
print("Gender summary in cluster 1:")
print(gender_summary1)

print("Product summary in cluster 1:")
print(product_summary1)

print("Numeric summary in cluster 1:")
print(numeric_summary1)

# Filter Cluster2
label2_dd<- dd %>% filter(label == 2)
# Summary of categorical variables (gender and product)
gender_summary2 <- label2_dd %>%
  group_by(gender) %>%
  summarise(count = n())

product_summary2 <- label2_dd %>%
  group_by(product) %>%
  summarise(count = n())
# Summary of numerical variables (Quantity and Price)
numeric_summary2 <- label2_dd %>%
  summarise(
    mean_quantity = mean(Quantity, na.rm = TRUE),
    sd_quantity = sd(Quantity, na.rm = TRUE),
    mean_price = mean(Price, na.rm = TRUE),
    sd_price = sd(Price, na.rm = TRUE)
  )
# Print summaries
print("Gender summary in cluster 2:")
print(gender_summary2)

print("Product summary in cluster 2:")
print(product_summary2)

print("Numeric summary in cluster 2:")
print(numeric_summary2)

# Filter Cluster3 
label3_dd<- dd %>% filter(label == 3)
# Summary of categorical variables (gender and product)
gender_summary3 <- label3_dd %>%
  group_by(gender) %>%
  summarise(count = n())

product_summary3 <- label3_dd %>%
  group_by(product) %>%
  summarise(count = n())
# Summary of numerical variables (Quantity and Price)
numeric_summary3 <- label3_dd %>%
  summarise(
    mean_quantity = mean(Quantity, na.rm = TRUE),
    sd_quantity = sd(Quantity, na.rm = TRUE),
    mean_price = mean(Price, na.rm = TRUE),
    sd_price = sd(Price, na.rm = TRUE)
  )
# Print summaries
print("Gender summary in cluster 3:")
print(gender_summary3)

print("Product summary in cluster 3:")
print(product_summary3)

print("Numeric summary in cluster 3:")
print(numeric_summary3)
