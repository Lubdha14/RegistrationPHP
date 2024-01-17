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



Decision tree








Python
https://www.kaggle.com/code/usmanabbas/pima-dibetes-analysis/notebook

https://www.kaggle.com/code/anupaav/iris-species-classifier-neural-network




