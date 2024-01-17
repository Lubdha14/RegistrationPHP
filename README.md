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

Python
---
https://www.kaggle.com/code/usmanabbas/pima-dibetes-analysis/notebook

https://www.kaggle.com/code/anupaav/iris-species-classifier-neural-network

Register
--
connection.php
<?php
$servername='localhost';
$username='root';
$password='';
$dbname='database1';

$conn = new mysqli($servername, $username, $password, $dbname);
if($conn->connect_error){
die("Connect Failed" . $conn->connect_error);
}
 echo " ";

index.php
<?php 
include("connection.php");
include("login.php");
?>
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel = "stylesheet" type="text/css" href="style.css">
</head>
<body>
    <div id ="form">
        <h1>Login Form</h1>
        <form name="form" action="login.php" method = "POST">
            <label>Username</label>
            <input type = "text" id ="user" name="user"><br><br>
            <label>Password</label>
            <input type ="password" id ="pass" name="pass"><br><br>
            <input type="submit" id ="btn" value="Login" name=""submit/>
        </form>
    </div>
    
</body>
</html>

login.php
<?php
session_start();
include('connection.php');
if(isset($_POST['submit'])){
    $username=$_POST['user'];
    $password =$_POST['pass'];

    $sql="select * from login where username = '$username' and password = '$password' ";
    $result = mysqli_query($conn, $sql);
    $row = mysqli_fetch_array($result, MYSQLI_ASSOC);
    $count = mysqli_num_rows($result);
    if($count==1){ 
        //$_SESSION['username'] = $username;
        header("Location: welcome.php");
        exit();
     }
    else{
       echo '<script>
        window.location.replace= "index.php";
       alert("Login failed.");
         </script>';
        
    }
}

welcom.php
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <h1>Login Successful</h1>
</body>
</html>

style.css
body{
    background-color: blanchedalmond;
}
#form{
    background-color: white;
    width: 25%;
    margin: 120px auto;
    padding :50px;
    box-shadow: 10px 10px 5px rgb(82,11,77);
    border-radius: 6px;
}
#btn{
color:black;
background-color: antiquewhite;

}
