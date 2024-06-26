---
layout: project
type: project
image: img/ai4allorg_logo.jpg
title: "AI4ALL - Computer Vision in Cars"
date: 2022
published: true
labels:
  - AI
  - Computer Vision
  - Python
summary: "In collaboration with a dynamic team of individuals, including Anthony Lau, Briana Lee, Jarren Seson, and Joel Vanta, this initiative delved into the realm of computer vision within the automotive industry, particularly focusing on its application in self-driving cars. "
---
<p align="center">
  <img src='https://miro.medium.com/v2/1*s9raSe9mLeSSuxE3API-ZA.gif' HSPACE='20' VSPACE='20' width='600'>
</p>

## What is Computer Vision?
Computer vision is a multidisciplinary field dedicated to empowering computers with the ability to comprehend and interpret visual data, such as images and videos. Its objective is to mimic the human visual system, enabling machines to extract meaningful information from visual inputs. This involves the development of algorithms and models for tasks like image classification, where computers assign labels to images; object detection, which involves locating and identifying multiple objects in an image; and image segmentation, the process of dividing an image into distinct segments. Computer vision applications span various domains, including healthcare, autonomous vehicles, surveillance, and robotics, leveraging techniques from image processing, machine learning, and artificial intelligence to facilitate the understanding and interpretation of the visual world.<br>

## What were our Objectives?
The primary objectives of our project were threefold. Firstly, we aimed to showcase the applications of computer vision, particularly in the context of self-driving vehicles, to those who may not be familiar with its use. Secondly, our goal was to disseminate knowledge and provide accessible insights into the fundamentals of computer vision for a broader audience. Lastly, we sought to establish a secure environment for testing and implementing real-world applications, ensuring practicality and safety in our endeavors.<br>

## Zumi Bots
<img align='left' src='https://raw.githubusercontent.com/ktam808/ktam808.github.io/main/img/ZumiBot.png' width='150' HSPACE='10' VSPACE='10'>
In order to acheive our goal, we decided to use Robolink Zumi Ai Robots. The Robolink Zumi AI Robot Car is an educational robotics kit designed for hands-on learning in programming, artificial intelligence, and computer vision. Equipped with a camera and various sensors, the small robot car enables users to engage in practical exercises such as recognizing objects, following lines, and detecting obstacles. The programming interface, based on the Python language, empowers users to control the robot's movements and implement AI algorithms. With a focus on providing educational resources and tutorials, the kit caters to beginners, offering step-by-step guidance for those interested in exploring real-world applications of robotics and AI concepts.<br>

## Color Detection
In this captivating project with the Robolink Zumi AI Robot Car, the goal was to leverage the power of Zumi's camera to capture a diverse array of images showcasing favorite colors. The subsequent step involved coding to extract valuable color information, facilitating the labeling of each distinct color. The project further delved into the exciting realm of machine learning, where a model was trained on the color data, enabling Zumi to autonomously identify and categorize colors. Whether it was the vibrant hues of red, blue, or green, the trained model became a powerful tool to discern and react to each color uniquely. This hands-on exploration not only provided insight into computer vision principles but also opened the door for programming Zumi to exhibit different behaviors based on the recognized colors, resulting in a delightful and interactive experience.

<img align='right' src='https://raw.githubusercontent.com/ktam808/ktam808.github.io/main/img/ColorDetectionGraph.png' HSPACE='20' VSPACE='20' width='500'>

```python
﻿zumi.mpu.calibrate_MPU()
camera.start_camera()

while True:
  image = camera.capture()
  predict = knn.predict(image)
  screen.draw_text_center(predict)

  if (predict == 'Green'):
    zumi.forward()
  elif (predict == 'Red'):
    zumi.turn_right(180)
  else:
    zumi.stop()
camera.close()
```
<br>

## Object Detection
Zumi's advanced capabilities are heightened by its array of six Infrared (IR) sensors, strategically positioned across its structure. These sensors play a crucial role in Zumi's environmental perception, with each sensor meticulously indexed for ease of data interpretation. Specifically, IR 0 is located at the front right, IR 1 at the bottom right, IR 2 at the back right, IR 3 at the bottom left, IR 4 at the back left, and IR 5 at the front left. This organized configuration enables Zumi to precisely retrieve data from various directions, enhancing its intelligent responsiveness to the surrounding environment. Infrared, a form of electromagnetic radiation beyond the visible spectrum, serves as the medium for these sensors. While it may sound ominous, not all electromagnetic radiation is harmful. Visible light, a small portion of this spectrum, is what humans can perceive, with different colors corresponding to varying wavelengths. Zumi's IR sensors, adept at detecting waves beyond the visible spectrum, are integral to identifying objects that obstruct their path.
```python
while 1 == 1:
  ir_readings = zumi.get_all_IR_data()
  back_right_ir = ir_readings[2]
  back_left_ir = ir_readings[4]

  front_right_ir = ir_readings[0]
  front_left_ir = ir_readings[5]

  #screen.draw_text_center(back_right_ir)
  
  if front_left_ir < 100:
    zumi.reverse()
  if back_right_ir < 50:
    zumi.foward()
```
<br>

## Insights
While our project achieved some success, certain underlying issues persisted. Notably, a challenge emerged with the color blue, as the Zumi exhibited difficulties in accurate color detection. It consistently perceived blue even when there was no object present, or occasionally detected blue even in the presence of a different color. Additionally, a notable problem arose where the Zumi failed to initiate movement, even in the presence of an obstacle. We suspect that this issue may be rooted in a potential error within the camera or sensor functionality. Addressing these challenges will require further investigation and potentially refining the code or troubleshooting the hardware components to ensure optimal performance.<br>

*Please note that I used ChatGPT to improve grammar and spelling in this document.*
