# introduce
Hello everyone welcome to my **stats220** website!
I am from the University of Auckland majoring in **data science**. I like to take risks and explore new things🙌.
# About my image
The images I make are about Snoopy and it's always expressive😆. _That's my favorite cartoon._ Because Snoopy and his owner Charlie Brown always have a lot of fun happening. So I combined my life and studies to make images of him.
## My image(snoopy)
Below is my image. I made using the R package [{magick}](https://cran.r-project.org/web/packages/magick/vignettes/intro.html)
![snoopy](https://github.com/RuoqiZhang7/stats220/blob/main/snoopy.png)

_My inspiration came from my birthday last year, and I think Snoopy's picture can perfectly express the change of my mood_😊.

# **R code**
library(magick)
snoopy_one <- image_read("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTr1Zf-04yf2HHItKYYBRgfdAfy3Uv-apNBmw&usqp=CAU") %>%
  image_scale(300)
frame <- image_border(snoopy_one, "hotpink", "5x5")
happy_snoopy <- image_annotate(frame, "I am very happy",font = 'Trebuchet', size = 30, gravity = "southwest", color = "black", boxcolor = "yellow")  

snoopy_two <- image_read("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRHX9f6c1pfdPPCwtuaHdXiWTYBqPbvcJ9lzA&usqp=CAU") %>%
  image_scale(300)
fence <- image_border(snoopy_two, "red", "5x5")
anger_snoopy <- image_annotate(fence, "I am very angry",font = 'Palatino', size = 35, color = "#000080", gravity = "north")

snoopy_three <- image_read("https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS0BIBHjWtHi7c6AEbLRw2ih8tfvOvRBrDIXtRfUiCmMiBH2scFJbYvjhYTxa_9k7pvlFE&usqp=CAU") %>%
  image_scale(300)
blackboard <- image_border(snoopy_three, "yellow", "5x5")
surprise_snoopy <- image_annotate(blackboard, "surprise",font = 'Impact', size = 45, color = "hotpink", gravity = "south")

happy_text <- image_blank(width = 310, 
                          height = 310, 
                          color = "purple") %>%
  image_annotate(text = "Today is my birthday :)",
                 color = "pink",
                 size = 20,
                 font = "Comic Sans",
                 gravity = "center")

anger_text <- image_blank(width = 310, 
                         height = 310, 
                         color = "blue") %>%
  image_annotate(text = "I thought NO one remembered\n my birthday :(",
                 color = "pink",
                 size = 20,
                 font = "Comic Sans",
                 gravity = "center")

suprise_text <- image_blank(width = 310, 
                       height = 310, 
                       color = "orange") %>%
  image_annotate(text = "My parents bought a\n new car for me !?",
                 color = "red",
                 size = 20,
                 font = "Comic Sans",
                 gravity = "center")

first_row <- c(happy_snoopy, happy_text) %>%
  image_append()

second_row <- c(anger_snoopy, anger_text) %>%
  image_append()

third_row <- c(surprise_snoopy, suprise_text) %>%
  image_append()

c(first_row, second_row, third_row) %>%
  image_append(stack = TRUE)

all_snoopy <- image_read("http://localhost:11171/session/preview.jpeg?viewer_pane=1&capabilities=1&host=http%3A%2F%2F127.0.0.1%3A33616")
image_write(all_snoopy,path = "snoopy.png",format = "png")


