# About my meme

![](my_meme.png)

_I used R code and the .[{magick}](https://cran.r-project.org/web/packages/magick/vignettes/intro.html) package to create the meme._

## The motivation

## Adaption

```r
library(magick)

face <- image_read("https://amuletopublicidade.com.br/wp-content/uploads/2019/12/img-737631-gavin-mastodon20160913141473788865.jpg")

# small
small <- image_scale(face, 200) %>%
  image_annotate(text = "Who am I?", color = "#ffffff", size = 30, font = "Impact", gravity = "south")

#medium
medium <- image_scale(face, 300) %>%
  image_annotate(text = "Where am I?", color = "#ffffff", size = 35, font = "Impact", gravity = "south")

#large
large <- image_scale(face, 400) %>%
  image_annotate(text = "What should I do?", color = "#ffffff", size = 40, font = "Impact", gravity = "south")

#text
text <- image_blank(width = 900, height = 100, color = "#ffffff") %>%
  image_annotate(text = "When starting a new assignment...", color = "#000000", size = 60, font = "Impact", gravity = "center")

# faces
faces <- c(small, medium, large) %>%
  image_append()

#making the whole thing
meme <- c(faces, text) %>%
  image_append(stack = TRUE)

image_write(meme, "my_meme.png")
```
