---
title: ggseg
cms_exclude: true

# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2

# Optional header image (relative to `static/media/` folder).
header:
  caption: ""
  image: ""
---
As a cognitive neuroscience student with a background in psychology, I wasn't permitted to take the somewhat coveted neuroanatomy course that the neuroscience department offered at my undergraduate institution. This course was all the hype! Dissecting sheep brains, carefully studying brain structures with the help of atlases and coming out smelling like formaldehyde (too far?). Point is, I felt clearly disadvantaged given that I am aware of the functioning of structures such as the percuneus, inferior frontal gyrus and fornix but can't visualize them. 
While there are some great software available online, access is limited by one simple problem.... MONEY!!!


```{r packages }
##install.packages("patchwork")
##install.packages("ggseg3d")
# install.packages("plotly")
# install.packages("ggsegExtra")
library(ggseg3d)
library(ggseg)
library(ggplot2)
library(patchwork)
library(dplyr)
library(plotly)

```



```{r gg seg}

fig2A <- ggseg(position = "stacked") + 
  theme_dark() +
labs(title = "dk",
subtitle = "dark theme")

fig2B <- ggseg(view = "medial") + labs(title = "dk",
subtitle = "medial view")


fig2C <- ggseg(view = "medial", hemisphere = "left") +
labs(title = "dk",
subtitle = "medial left")

fig2D <- ggseg(position = "stacked") + theme_classic() +
labs(title = "dk",
subtitle = "classic theme")

fig2E <- ggseg(hemisphere = "left") + labs(title = "dk",
subtitle = "left hemisphere")


fig2F <- ggseg(atlas = aseg, view = "axial") +
labs(title = "aseg", subtitle = "axial view")

fig2F <- ggseg(atlas = aseg, view = "axial") +
labs(title = "aseg", subtitle = "axial view")

##using patchwork
(fig2A | fig2B | fig2C) / (fig2D | fig2E | fig2F) +
  plot_annotation(tag_levels = 'a')

ggseg(mapping=aes(file=region),colour="black")+
  scale_fill_brain("dk")+
  theme(legend.justification = c(1,0),legend.position = "bottom",
        legend.text = element_text(size=5))+
  guides(fill=guide_legend(ncols=3))

fig9 <- ggseg3d(atlas = aseg_3d, na.alpha = .5) %>% 
add_glassbrain("left",colour = "#cecece",
      opacity = 0.3) %>% 
pan_camera("left lateral")
fig9



ggseg(mapping = aes(fill = region), colour = "black") +
  scale_fill_brain("dk") +
  theme(legend.justification = c(1, 0),
        legend.position = "bottom", legend.text = element_text(size = 5)) +
guides(fill = guide_legend(ncol = 3))


ggseg (atlas = "aseg",
mapping = aes(fill = region)) +
  theme(legend.justification = c(1, 0), legend.position = "bottom" , legend.text = element_text(size = 5)) +
  guides(fill = guide_legend(ncol = 3))
                                 
```

