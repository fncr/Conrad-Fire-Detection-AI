# Fire Detection AI
I am working with a raspberry pi that will feed a live video stream into a machine learning model that returns and determines whether there is a fire in the raspberry pi's FOV

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Conrad Wu | Saratoga High School | Electrical(?) Engineering | Incoming Senior

![Headstone Image](https://cdn.discordapp.com/attachments/731991179599675602/855536300277891093/shimnzo.png)
  
# Final Milestone
By the end of this project I want to be able to put the raspberry pi and a camera on a drone that can fly around and find fires, and even determine the class of fire. 

[![Final Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1612573869/video_to_markdown/images/youtube--F7M7imOVGug-c05b58ac6eb4c4700831b2b3070cd403.jpg )](https://www.youtube.com/watch?v=F7M7imOVGug&feature=emb_logo "Final Milestone"){:target="_blank" rel="noopener"}

# Second Milestone
I've been able to write some python programs that take images using the raspberry pi, send images to nanonets, get that image back with an inference with where the fire is in the image, then present an image to the user with a box drawn around where the model thinks the fire is. I started off with just taking 10 pictures and saving them to a directory, then had a different program parse through the directory and feed all of the images to nanonets.
![Working Model](https://lh5.googleusercontent.com/YndtX9mm7Z2gCPpmGnnn5Ced1T2f-rCcHEoLss_9mTI8EdraqtrYzcsTIL_J_p_krwyn7Jo32Tix7zVWPpEKQuXKuXDWFgWRHF6asyxhBpyg2tOkNjtM0ilNieRGVcIW2DXi8nVc)
Now I have a program that combines the taking images and feeding to nanonets. It displays an inference, then takes a picture and gets a response from Nanonets, then right before displaying the image it kills the previous one, thus making a sort of pseudo-video


[![Third Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1612574014/video_to_markdown/images/youtube--y3VAmNlER5Y-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=y3VAmNlER5Y&feature=emb_logo "Second Milestone"){:target="_blank" rel="noopener"}
# First Milestone
I set up the raspberry pi and was able to run python scripts and tensor flow. I was also able to use NanoNets to develop a model that can detect fires. Initially I tried hosting the model and processing on the raspberry pi, but all of the guides I followed were outdated, and NanoNets' servers seem to have better processing power than the Raspberry Pi and has updated documentation

[![First Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1612574014/video_to_markdown/images/youtube--HELhTF0Dyzc-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=HELhTF0Dyzc "First Milestone"){:target="_blank" rel="noopener"}
