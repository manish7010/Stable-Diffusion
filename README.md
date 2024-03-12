Task: Text to Image Generation


We implement all models using Huggingface diffusers 

Two prompts are used throughout this task
The first prompt -- has good detail of the person as well as the background, outdoor setting
The second prompt -- has excellent detail of the person but less about background, studio setting
Baseline:- 
We First Started with two popular stable-diffusion models, both having an output image size of 512* 512.
runwayml/stable-diffusion-v1-5
CompVis/stable-diffusion-v1-4
We conducted experiments using both float32 and float16 data types. While float16 resulted in slightly inferior image quality, its advantage lies in its smaller size and faster processing speed.
We attempted to generate an image with dimensions of 2048 x 2048 using the float32 data type but encountered a CUDA error. Conversely, float16 allowed for image generation; however, the output quality suffered, with multiple persons appearing distorted within the image.
After generating the images, we upscale the image to 2048*2048
For the first prompt in which the background is complex (outdoor setting), the generated image is of poor quality and lacks realism.
For the second prompt, in which the background is simple(studio-setting), the generated image is of good quality and looks natural.






Improving Quality:- 
we use the popular stabilityai/stable-diffusion-xl-base-1.0 model which generates high-quality 1024 * 1024 image
We can only experiment with the half-precision(fp-16) model.
The generated images for both the prompts are of good quality and look natural.
The time taken to generate both images with 50 inference steps is 88 sec.

Improving Speed:-
To reduce the time to generate images, we use the popular "ByteDance/SDXL-Lightning", which generates high-quality 1024 * 1024 image
It gives great results in just 2/4/8 inference steps. We utilised the 8-step checkpoints.


The time taken to generate both images with 8 inference steps is just 13  sec.


Lora Models:-
We also utilised the stabilityai lora model to reduce the model size and even reduce image generation time.
While the quality of images slightly decreases, mainly for the first-prompt (outdoor setting), the image quality is still good
The time taken to generate both images with 8 inference steps is just 10  sec.



