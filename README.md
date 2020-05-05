# FuntionToGrepandBindtoDF
user Defined Function to Grep and Bind the value to the Data Frame
extractTitle <- function(name) {
  name <- as.character(name)
  
  if (length(grep("Miss.", name)) > 0) 
  {
    return("Miss.")
  }
  else if (length(grep("Master.", name)) > 0)
  {
    return("Master.")
  }
  else if (length(grep("Mrs.", name)) > 0)
  {
    return("Mrs")
  }
  else if (length(grep("Mr.", name)) > 0)
  {
    return("Mr.")
  }
  else {
    return("Other")
  }
  
}

#now extract the title from each row.name and bind it back to the data frame

getTitleName("Futrelle, Master. Jacques Heath (Lily May Peel)")

#View(titanic.bind)

titles<- NULL
for (i in 1:nrow(titanic.bind))
{
  titles <- c(titles,extractTitle(titanic.bind[i,"Name"]))
}
#bind the extracted values to the data frame
titanic.bind$title<-as.factor(titles)
#view the binded value is added
View(titanic.bind)
