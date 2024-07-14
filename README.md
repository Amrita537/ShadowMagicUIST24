# ShadowMagic
This repository contains row resolution dataset that has been collected from a comic company dedicated for the project "Stage-by-stage and Step-by-step: Designing Human-AI Collaborative Support for Professionals’ Comic Shadowing".
There are N number of flat images and line drawing. For each flat, there are shadow image examples from four light directions (Left, Right, Top, Back). The image resolution is X*Y.

Paper link (Will be updated soon)

The original dataset to train the AI models has been collected from the professionals of a single company who made shadows dedicated to this project. After S1, they first prepared 1,000 existing flat-colored line drawings made previously. Ofthese, they made 2 directions (left and right) of shadows for 960 and 4 directions for 40. This was because left and right had more variability which required more examples for generating to meet our quality standard while top and bottom directions were fairly consistent.

This dataset has been used in the two models below:
1. Initial shadow prediction model: 
  A custom dataset of 342 images was created, with shadows annotated for various light directions. Initial shadow predictions were generated using Stable Diffusion XL and the Reproduction Model. These predictions were refined through conditional image translation by ControlNet, which was specifically trained for shadow prediction. The resolution of the refined shadows was then upscaled using Real-ESRGAN. Finally, an iterative shrinking algorithm allowed users to fine-tune the shadow size, ensuring high-quality, professional-standard shadow generation for digital comics. 

2. Character semantic segmentation model:
The process begins with fine-tuning the YOLOv5 segmentation model on a dataset of 614 annotated images to detect semantic segments such as hair, face, cloth, arm, and objects. The model outputs bounding boxes and approximate masks for these segments. To achieve precise semantic segment contours, the approximate masks are replaced with more accurate ones derived from input flat color images, by merging regions with significant overlap. This refined segmentation allows users to selectively adopt shadow suggestions based on the identified scene semantics.

![image](https://github.com/user-attachments/assets/a009b070-4a9c-47a4-9155-760ad0ee64d8)
![frontend1_2](https://github.com/user-attachments/assets/ba250ca1-4bd1-4b27-aa2f-d488719658fb)
