CREATE DATABASE atlab1;
USE atlab1;
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    username VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL,
    password VARCHAR(255) NOT NULL
);
select * from users


R Prograam
ui.r
--
shinyUI(
  pageWithSidebar(
  
    headerPanel("My First Shiny App"),
    
    sidebarPanel(
    
      selectInput("Distribution", "Please select Distribution type",
      
                  choices = c("Normal","Exponential" )),
                  
      sliderInput("SampleSize", "Please select Sample size",
      
                  min=100, max=5000,value=1000, step=100),
                  
      conditionalPanel(condition="input.Distribution=='Normal'", 
      
                       textInput("Mean", "Please select Mean", 10),
                       
                       textInput("id", "Please select Standard Deviation", 3)),
                       
      conditionalPanel(condition="input.Distribution=='Exponential'",
      
                       textInput("lamba", "Please select Exponential Lamba", 1))
      
      
    ),
   
    mainPanel(
     
      plotOutput("myPlot")
    
    )

  )

)



server.r  
--
shinyServer(function(input, output, session) {

  output$myPlot <- renderPlot({
   
    distType <- input$Distribution

    size <- input$SampleSize
    
    if (distType == 'Normal') {
    
      randomVec <- rnorm(size, mean = as.numeric(input$Mean), sd = as.numeric(input$id))
    
    } else {
    
      randomVec <- rexp(size, rate = 1/as.numeric(input$lamba))
    
    }
    
    hist(randomVec, col = "blue")
  
  })

})

Commands
-
library(shiny)

setwd("directoryname")

runApp()

Decision tree
--
library(rpart)

library(rpart.plot)

library(party)

print(head(readingSkills))

input.dat<-readingSkills[c(1:105)]

output.tree<-ctree(nativeSpeakers~age+shoeSize+score,
                   data=input.dat)

plot(output.tree)

dev.off()

Iris Dataset
--
-# Load required libraries
library(party)
library(partykit)

-# Print the first few rows of the iris dataset
print(head(iris))

-# Create a subset of the iris dataset (e.g., first 120 rows)
input_data <- iris[1:120, ]

-# Build a conditional inference tree model
output_tree <- ctree(Species ~ Sepal.Length + Sepal.Width + Petal.Length + Petal.Width, data = input_data)

-# Plot the resulting tree
plot(output_tree)

-# Close the device where the plot is displayed
dev.off()

Python
---
https://www.kaggle.com/code/usmanabbas/pima-dibetes-analysis/notebook

https://www.kaggle.com/code/anupaav/iris-species-classifier-neural-network

https://tinyurl.com/kyp6vcv2



}
