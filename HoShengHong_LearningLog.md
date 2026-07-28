# Learning Log Part B


## Technique 1: Transfer Learning with MobileNetV2

**The Concept**:
MobileNetV2 is a model pre-trained on 1.4 million images. Instead of building a CNN 
from scratch like in Part A, I borrowed its knowledge and added my own layers on top 
for the 53 card classes.

**The Learning**
- MobileNetV2 already knows how to detect edges, textures and shapes
- I froze its weights first so only my new layers trained
- Then unfroze the last 50 layers and fine-tuned at a lower learning rate (0.0001)
- This was the biggest improvement — accuracy jumped from 70% to 91%

I learned that MobileNetV2 works by reusing features like edges and textures it already 
learned from 1.4 million images — by freezing its layers first then fine-tuning the 
last 50, the model adapted to playing cards without losing its pretrained knowledge, 
which is why accuracy jumped from 70% to 91%.

**Implementation**


![alt text](image.png)





## Technique 2: Label Smoothing

**The Concept**:
Instead of training the model to be 100% confident on each card, Label Smoothing 
softens this to 90% and spreads the remaining 10% across other classes.

**The Learning**
- Normally the model targets 100% confidence on the correct class
- Label Smoothing reduces this to 90%, leaving room for uncertainty
- Prevents the model from being overconfident on training data
- Helped the model generalise better to unseen cards during testing

I learned that Label Smoothing works by softening how confident the model is allowed 
to be during training, so instead of being fully certain it leaves a little room for 
doubt, and this small change actually helped my model do better on cards it had never 
seen before.

**Implementation**


![alt text](image-3.png)



## Technique 3: Cosine Annealing

**The Concept**:
Instead of keeping the learning rate fixed throughout training, Cosine Annealing 
automatically decreases it smoothly over time following a cosine curve.

**The Learning**
- Learning rate starts high so the model learns quickly at the beginning
- It then gradually decreases following a cosine wave pattern
- Prevents the model from overshooting good solutions near the end of training
- Especially useful during fine-tuning where a high learning rate can destroy pretrained weights

I learned that Cosine Annealing controls how much the model adjusts itself each step 
by starting with large updates early on so it learns fast, then gradually reducing 
them so it can settle into a precise solution without overshooting — this was especially 
important during fine-tuning so the pretrained weights weren't accidentally destroyed.

**Implementation**


![alt text](image-4.png)



## Technique 4: Grad-CAM

**The Concept**:
Grad-CAM is a visualisation technique that generates a heatmap showing which parts 
of the card the model focused on when making a prediction. It is used for visual 
explainability only and does not directly improve accuracy.

**The Learning**
- Uses gradients from the last convolutional layer to find important regions
- Red areas mean the model focused heavily there
- Blue areas mean the model mostly ignored that part
- Helped me confirm the model was looking at the right things like the suit and number

I learned that Grad-CAM works by looking at which parts of the image the model 
reacted to the most, and from the heatmaps I could see my model was correctly 
focusing on the card's suit and number rather than the background.

**Implementation**: 2 Images for one cell block.


![alt text](image-5.png)

![alt text](image-6.png)