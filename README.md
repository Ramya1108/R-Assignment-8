CODE:

# Load required packages

install.packages("plyr")

library(data.table)

library(plyr)



# Import dataset

Student <- read.table("C:/Users/Ramya Challa/Desktop/Assignment6_Dataset.txt", header = TRUE, sep = ",")

# Calculate mean using Sex as the category

StudentAverage <- ddply(Student, "Sex", summarise, Grade.Average = mean(Grade))

# Write output to a file

write.table(StudentAverage, "StudentAverage.txt", sep = ",", row.names = FALSE)

# Filter the original data set to include only data for which the student name contains the letter "i"

i_students <- subset(Student, grepl("i", Student$Name, ignore.case = TRUE))

# Write names containing "i" to a CSV file

write.csv(i_students$Name, "i_students_names.csv", row.names = FALSE)

# Write the filtered dataset to a CSV file using file.choose() and subset()

write.csv(i_students, "Datasubset.csv",sep = ",")



EXPLANATION:

1.Package Installation and Loading: It begins by installing and loading necessary packages like plyr and data.table to enable data manipulation and analysis.

2.Data Import: It imports a dataset named "Assignment6_Dataset.txt" from the specified file path into R using read.table(). The dataset is assumed to have a header row indicating variable names and is comma-separated.


 3.Mean Calculation by Category: The code calculates the mean grade for each category of 'Sex' using the ddply() function from the plyr package. It creates a new dataframe StudentAverage containing the calculated mean grades.


 4.Writing Output to Files: It writes the calculated mean grades to a file named "StudentAverage.txt" with comma-separated values using write.table().


 5.Filtering Data: It filters the original dataset (Student) to include only rows where the student name contains the letter "i". This is achieved using the subset() function along with the grepl() function for pattern matching.


 6.Writing Filtered Names to CSV: The names of students containing the letter "i" are written to a CSV file named "i_students_names.csv" using write.csv().


 7.Writing Filtered Dataset to CSV: The filtered dataset (i_students) is written to another CSV file named "Datasubset.csv" using write.csv(), with comma-separated values.
