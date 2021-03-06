---
title: gg_seg

# **gg_seg**



  As a neuroscience grad student with a background in psychology, I wasn't permitted to take the somewhat coveted neuroanatomy course that the neuroscience department offered at my undergraduate institution. This course was all the hype! Dissecting sheep brains, carefully studying brain structures with the help of atlases and coming out smelling like formaldehyde (too far?). Point is, I felt clearly disadvantaged given that I am aware of the functioning of structures such as the percuneus, inferior frontal gyrus and fornix but can't visualize them. 
  
  
  While there are some great software available online, access is limited by one simple problem.... MONEY!!!
Just when I was about to buy an atlas, I came across this incredibly cool feature in r that lets you visualize the brain in a 2D **and** a 3D fashion. 

  The r package that let's you do a 2D analysis is called ggseg. From an input standpoint, it is like the ggplot package but uses inbuilt atlases to display the brain from various vantage points. 

### Stacked Image
This is just a simple (boring) stacked image

**ggseg(atlas="dk",position = "stacked") +**
  **theme_classic() +**
  
  
  
  
  `static/uploads/all.png`
  

### A Medial view with the aseg atlas 


***ggseg(atlas="aseg",position = "stacked") + theme_classic() +***


***labs(title = "aseg_atlas",***
***subtitle = "classic theme")***

  `static/uploads/medial.png`



### Region Fill

You can also add legends and fill areas on the plot according to brain regions  

ggseg(mapping=aes(file=region),colour="white")+
  ***scale_fill_brain("aseg")+***
  
  ***theme(legend.justification = c(1,0),legend.position = "right",***
  
  ***legend.text = element_text(size=6))+***
        
  ***guides(fill=guide_legend(ncols=3))***
  
    `static/uploads/white.png`
    
### 2D subcortical Structures 


    `static/uploads/subcortical.png`
  
  
 ***Now for the coolest one***
 
 The 3D atlas...
 
 In addition to the arguments taken by a 2D atlas, this takes the arguments of opacity and color for the background 


The functionality is especially great for visualizing the sub cortical structures that are buried deep under the cortex. What's more? it also labels them..

   
   
    `static/uploads/rename.png`
    
    
    
    
**ggseg (atlas = "aseg",**

**mapping = aes(fill = region)) +**

  ***theme(legend.justification = c(1, 0), legend.position = "bottom" , legend.text = element_text(size = 5)) +***
  
  ***guides(fill = guide_legend(ncol = 3))***
  
`static/uploads/glass.png`
  
_Suffice to say that I won't be needing an atlas anymore... :)_ 
                                 

