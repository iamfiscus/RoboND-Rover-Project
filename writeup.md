## Project: Search and Sample Return
### Writeup Template: You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---


**The goals / steps of this project are the following:**  

**Training / Calibration**  

* Download the simulator and take data in "Training Mode"
* Test out the functions in the Jupyter Notebook provided
* Add functions to detect obstacles and samples of interest (golden rocks)
* Fill in the `process_image()` function with the appropriate image processing steps (perspective transform, color threshold etc.) to get from raw images to a map.  The `output_image` you create in this step should demonstrate that your mapping pipeline works.
* Use `moviepy` to process the images in your saved dataset with the `process_image()` function.  Include the video you produce as part of your submission.

**Autonomous Navigation / Mapping**

* Fill in the `perception_step()` function within the `perception.py` script with the appropriate image processing functions to create a map and update `Rover()` data (similar to what you did with `process_image()` in the notebook).
* Fill in the `decision_step()` function within the `decision.py` script with conditional statements that take into consideration the outputs of the `perception_step()` in deciding how to issue throttle, brake and steering commands.
* Iterate on your perception and decision function until your rover does a reasonable (need to define metric) job of navigating and mapping.  

[//]: # (Image References)

[image1]: ./misc/rover_image.jpg
[image2]: ./calibration_images/example_grid1.jpg
[image3]: ./calibration_images/example_rock1.jpg
[calibration_data]: ./output/docs/calibration_data.png
[perspective_transform]: ./output/docs/perspective_transform.png
[color_threshold]: ./output/docs/color_threshold.png
[threshold_arrow]: ./output/docs/threshold_arrow.png
[find_rock]: ./output/docs/find_rock.png
[result]: ./output/docs/test_mapping.gif

## [Rubric](https://review.udacity.com/#!/rubrics/916/view) Points
### Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

---
### Writeup / README

#### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one.  You can submit your writeup as markdown or pdf.  

You're reading it!

### Notebook Analysis
#### 1. Run the functions provided in the notebook on test images (first with the test data provided, next on data you have recorded). Add/modify functions to allow for color selection of obstacles and rock samples.
The first step in this process was to create calibration images. Below are examples of those beginning with the left, which is an example of mapping a 1m X 1m grid to the surface of Mars. On the right is an example of of a yellowish rock which we use as the basis to create a rock detection function.

![Calibration Data][calibration_data]

Next is creating a perspective transform which is below on the left. On the left is the same transform with a mask applied.

![Perspective Transform & Inverted][perspective_transform]

After transforming we create a color threshold to help determine the path, obstacle or rock.

![Color Threshold][color_threshold]

Below shows the color threshold on the left and on the left is the predicted navigable path for the rover to go.

![Navigatable Path][threshold_arrow]

`find_rock()` which uses the color threshold to identify the yellowish colored rock.

![Find Rock][find_rock]


#### 1. Populate the `process_image()` function with the appropriate analysis steps to map pixels identifying navigable terrain, obstacles and rock samples into a worldmap.  Run `process_image()` on your test data using the `moviepy` functions provided to create video output of your result.
Below is my final result of test mapping video.

![Mapping Result][result]
### Autonomous Navigation and Mapping

#### 1. Fill in the `perception_step()` (at the bottom of the `perception.py` script) and `decision_step()` (in `decision.py`) functions in the autonomous mapping scripts and an explanation is provided in the writeup of how and why these functions were modified as they were.

Since this was the first project I got a bit stuck. After watching the video it helped me figure out how to use the lectures in the future and write up `perception_step()`.

As stated above I created a `find_rock()` function which uses color threshold to identify rocks.

Lastly I didn't touch `decision_step()` which is the function that moves the rover forward unless is sees an obstacle. If encountering an obstacle it will look the at the and make a decision to stop, go left, right or turn around. I realize I could add to the logic in order to make more decision including about rocks. 


#### 2. Launching in autonomous mode your rover can navigate and map autonomously.  Explain your results and how you might improve them in your writeup.  

Using the approach from the video I was able to achieve the necessary percentage of mapping to pass.

Unfortunately I didn't have time to pick and place the rocks, then return to the starting location. Also I could have added variables to the decision steps.
