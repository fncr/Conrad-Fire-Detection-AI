# Fire Detection AI
I am working with a raspberry pi that will feed a live video stream into a machine learning model that returns and determines whether there is a fire in the raspberry pi's FOV

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Conrad | Saratoga High School | Electrical(?) Engineering | Incoming Senior

![Headstone Image](https://github.com/fncr/ConradWu-Fire-Detection-AI/blob/gh-pages/images/68747470733a2f2f6c68352e676f6f676c6575736572636f6e74656e742e636f6d2f596e647458396d6d375a32674350706d476e6e6e35436564315432662d72436348456f4c73735f396d54493845647261717.png)

# Links and Resources
* [My Github Repo](https://github.com/fncr/Raspi-Fire-Detection)
* [Basic Guide to Using NanoNets](https://medium.com/nanonets/how-to-easily-detect-objects-with-deep-learning-on-raspberrypi-225f29635c74)
* [Using and accessing the Raspberry Pi Camera](https://picamera.readthedocs.io/en/release-1.13/recipes1.html)
* [Getting Tensorflow on the Raspberry Pi](https://www.makeuseof.com/tag/image-recognition-tensorflow-raspberry-pi/)
* [Using TensorFlow Lite on Raspberry Pi, Ended Up Being Outdated](https://www.digikey.com/en/maker/projects/how-to-perform-object-detection-with-tensorflow-lite-on-raspberry-pi/b929e1519c7c43d5b2c6f89984883588)

# Second Session
Below milestones take place in the second session of BlueStamp. This session revolved around applying the raspberry pi to a larger product that could be useful in detecting forest fires early.

## Fifth Milestone
Got text message functional. This includes getting and sending GPS data from the raspberry piand sending an image of the fire to the user. Also has some code to send one text per fire based on the location rather than every frame that the machine detects a fire in.

## [Fourth Milestone](https://www.youtube.com/watch?v=M1F8t6Ycy2U)
In trying to move away from NanoNets to try to avoid hitting its api call limit and to hopefully get more images processed faster, I set up a personal server with Tensorflow to run object detection rather than NanoNets' servers that might be more powerful but will cut down on latency.

# First Session
Below milestones take place in the first session of Bluestamp. This session I focused mostly on the machine learning and raspberry pi centric parts of the project

## [Third Milestone](https://www.youtube.com/watch?v=KC2r7oby-mg)
![working stream](https://github.com/fncr/Conrad-Fire-Detection-AI/blob/gh-pages/images/workingPrototypeDetect.png)
The Raspberry PI now combines the two aformentioned scripts using OpenCV to create a live video stream with boxes drawn around a fire in each frame. I updated the model which now uses around 500 images as opposed to 50 prior. It tracks fire pretty well, though the framerate leaves something to be desired but there isn't much I can do as that's mostly limitations with computational power and data transfer.
```ruby
import cv2, json, requests, os
import time

def feed(model_id, api_key, n):
    # make a prediction on the image
    image_path = n

    url = 'https://app.nanonets.com/api/v2/ObjectDetection/Model/' + model_id + '/LabelFile/'

    data = {'file': open(image_path, 'rb'),    'modelId': ('', model_id)}

    response = requests.post(url, auth=requests.auth.HTTPBasicAuth(api_key, ''), files=data)
    response = json.loads(response.text)

    prediction = response["result"][0]["prediction"]

    return prediction


def useCV(model_id, api_key, n):
    cap = cv2.VideoCapture(0)
    while True:
        _, frame = cap.read()
        cv2.imwrite(n, frame)
        prediction = feed(model_id, api_key, n)

        # draw boxes on the image
        for i in prediction:
            if i["score"] > .75:
                percentVal = 'fire: ' + str(i["score"]*100) + '%'
                cv2.rectangle(frame,(i["xmin"],i["ymin"]+3), (i["xmax"],i["ymax"]), (0, 255, 0), 3)
                cv2.putText(frame, percentVal, (i["xmin"], i["ymin"]), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 255, 0), 2)
		cv2.rotate(frame, cv2.cv2.ROTATE_180_CLOCKWISE)
        cv2.imshow("Frame", frame)
        if cv2.waitKey(1) & 0xFF == ord('q'):
            break

    cap.release()
    cv2.destroyAllWindows()

def main():
    model_id = os.environ.get('NANONETS_MODEL_ID')
    api_key = os.environ.get('NANONETS_API_KEY')

    n = '/home/pi/Projects/Python/NanoNets/FireDetection/FireImages/Frame.jpg'

    useCV(model_id, api_key, n)

main()
```

## [Second Milestone](https://www.youtube.com/watch?v=tQt0Xg7fepw)
I've been able to write some python programs that take images using the raspberry pi, send images to nanonets, get that image back with an inference with where the fire is in the image, then present an image to the user with a box drawn around where the model thinks the fire is. I started off with just taking 10 pictures and saving them to a directory, then had a different program parse through the directory and feed all of the images to nanonets.
Now I have a program that combines the taking images and feeding to nanonets. It displays an inference, then takes a picture and gets a response from Nanonets, then right before displaying the image it kills the previous one, thus making a sort of pseudo-video

![Bad NanoNets](https://github.com/fncr/ConradWu-Fire-Detection-AI/blob/gh-pages/images/shimnzo.png)

## [First Milestone](https://www.youtube.com/watch?v=HELhTF0Dyzc "First Milestone")
I set up the raspberry pi and was able to run python scripts and tensor flow. I was also able to use NanoNets to develop a model that can detect fires. Initially I tried hosting the model and processing on the raspberry pi, but all of the guides I followed were outdated, and NanoNets' servers seem to have better processing power than the Raspberry Pi and has updated documentation
