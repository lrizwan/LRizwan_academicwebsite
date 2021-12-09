---
title: Blog Post 1


{r packages }
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


# View.
#   1 = List
#   2 = Compact
#   3 = Card
view: 2

---
