# Fire Detection AI
I am working with a raspberry pi that will feed a live video stream into a machine learning model that returns and determines whether there is a fire in the raspberry pi's FOV

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Conrad Wu | Saratoga High School | Electrical(?) Engineering | Incoming Senior

![Headstone Image](https://cdn.discordapp.com/attachments/731991179599675602/855536300277891093/shimnzo.png)

# Links and Resources
(https://medium.com/nanonets/how-to-easily-detect-objects-with-deep-learning-on-raspberrypi-225f29635c74 "Basic Guide to Using NanoNets")
(https://picamera.readthedocs.io/en/release-1.13/recipes1.html "Using and accessing the Raspberry Pi Camera")
(https://www.makeuseof.com/tag/image-recognition-tensorflow-raspberry-pi/  "Getting Tensorflow on the Raspberry Pi")
(https://www.digikey.com/en/maker/projects/how-to-perform-object-detection-with-tensorflow-lite-on-raspberry-pi/b929e1519c7c43d5b2c6f89984883588 "Using TensorFlow Lite on Raspberry Pi, Ended Up Being Outdated")



# Final Milestone
The Raspberry PI now combines the two aformentioned scripts using OpenCV to create a live video stream with boxes drawn around a fire in each frame. I updated the model which now uses around 500 images as opposed to 50 prior. It tracks fire pretty well, though the framerate leaves something to be desired but there isn't much I can do as that's mostly limitations with computational power and data transfer. 

[![Final Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1612573869/video_to_markdown/images/youtube--F7M7imOVGug-c05b58ac6eb4c4700831b2b3070cd403.jpg )](https://www.youtube.com/watch?v=F7M7imOVGug&feature=emb_logo "Final Milestone"){:target="_blank" rel="noopener"}

# Second Milestone
I've been able to write some python programs that take images using the raspberry pi, send images to nanonets, get that image back with an inference with where the fire is in the image, then present an image to the user with a box drawn around where the model thinks the fire is. I started off with just taking 10 pictures and saving them to a directory, then had a different program parse through the directory and feed all of the images to nanonets.
![Working Model](https://lh5.googleusercontent.com/YndtX9mm7Z2gCPpmGnnn5Ced1T2f-rCcHEoLss_9mTI8EdraqtrYzcsTIL_J_p_krwyn7Jo32Tix7zVWPpEKQuXKuXDWFgWRHF6asyxhBpyg2tOkNjtM0ilNieRGVcIW2DXi8nVc)
Now I have a program that combines the taking images and feeding to nanonets. It displays an inference, then takes a picture and gets a response from Nanonets, then right before displaying the image it kills the previous one, thus making a sort of pseudo-video

https://github.com/fncr/Raspi-Fire-Detection

My code can be found above

[![Third Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1612574014/video_to_markdown/images/youtube--y3VAmNlER5Y-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=tQt0Xg7fepw "Second Milestone"){:target="_blank" rel="noopener"}
# First Milestone
I set up the raspberry pi and was able to run python scripts and tensor flow. I was also able to use NanoNets to develop a model that can detect fires. Initially I tried hosting the model and processing on the raspberry pi, but all of the guides I followed were outdated, and NanoNets' servers seem to have better processing power than the Raspberry Pi and has updated documentation

[![First Milestone]()](https://www.youtube.com/watch?v=HELhTF0Dyzc "First Milestone"){:target="_blank" rel="noopener"}
