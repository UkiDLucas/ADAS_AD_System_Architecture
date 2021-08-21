# ADAS and Autonomous Driving System Architecture



Last edited on August 20, 2021

by Uki D. Lucas



## Motivation

Computer Science engineers who switch to the field of **Advanced Driver Assistance Systems (ADAS)** and **Automated Driving (AD)** usually have a rich set of skills, but generally lack the specific to this field **System Architecture** perspective. This situation may change in the next few years as companies like Tesla publicize their designs (see reference #1), but today such designs remain somewhat esoteric. 

Many startups prototype their ideas on Linux general-purpose computers (laptops, Nvidia Xavier) to realize months or years later that their **prototype has no chance of running in a low-cost, hardware-accelerated, functional safety-oriented, embedded system**. The right design from the ground up is the key.

This text attempts to be a practical guide while referencing **publicly available information** in the reference section at the end.



## What is function of a System Architect?

The System Architect's job is to ensure that the whole system, including hardware, peripherals, software, Human-Machine Interfaces (HMI), remote services, as well manufacturing, **delivers a product that functions well when combined together**. The System Architect may not know the details of implementation of a particular component, but should investigate if that component would function well in the final product. The System Architect usually provides data flow, module-interaction-level diagrams and system requirements specifications (SRS) from which the user experience (UX) experts, mechanical, electronic and software architects can design their particular domains.



## Feature-level components of ADAS/AD

There are many subsystems that comprise of ADAS/AD domain. 

Here are some of the examples of features from most common to futuristic:

- surround view (SV)
- Augmented Reality with a center-stack display or heads-up display (HUD) 
- rear eMirror, Camera Monitoring System (CMS)
- side eMirrors, Camera Monitoring System (CMS)
- lane keep assist (LKA)
- pedestrian and large animal detection (component)
- obstacle detection (component)
- emergency breaking system (EBS)
- cross-traffic alert (CTA)
- curb detection (component)
- street-sign detection (component)
- free-space detection (component)
- automated cruise control (ACC)
- driver monitoring system (DMS)
- occupant monitoring system (OMS)
- automated park assist (APA)
- automated valet parking (AVP)
- valet parking - remote summon 
- L2 automated highway driving, driver supervision required
- L3 any road autonomy, driver supervision required
- L4 any road autonomy, driver controls provided, driver supervision not required
- L5 full autonomy, no driver controls provided

As you can see the field is very large and constantly growing, this field is a true bonanza for a motivated engineer.



## Design Assumptions



The traditional approach is to provide a **low-cost electronic control unit (ECU) per each feature**, but the tendency in the market is to combine many of these into more powerful Domain Controller that host multiple features are **designed based on the safety level desired**.

In this book I will explore a **Domain Controller that meets safety levels up to L2 of autonomy** and then explore design of **L3+ based on the Tesla design** as that is the only one that is publicly available at this time.



## Value provided

In order to write this book I had to spend many weekends and burn much of the midnight oil. 

The field of automated driving is changing constantly and updating the book takes effort and motivation. 

The author assumes there will be very limited group of people who are interested in reading this book, so every copy sold will make the motivational difference in order to continue the effort.

This book is sold with license for a single person who paid for it. Sharing any part of the content is a violation of a copyright and an ethical trespass. 

If you would like to buy this book to share it with your team as PDF or ebook, please contact the author for a deep group discount.  

If you have obtained a free copy of this book please consider purchasing  a copy from Amazon Kindle to show your support for author's efforts. This book costs a fraction of what a System Architect makes in one hour, please consider it.

I hope you will use this book as a reference. If you previously purchased the book on Kindle, occasionally delete it from your device and download it again to get an updated version.



## Contributions by the readers

The architects are very opinionated bunch, every company has different approach to the design, so I expect a metric ton of criticism. 

Please consider the following, if you provide me a correction in a constructive format such as "You have written that X is Y, but based on [URL included] the X is really Z" than I will include the correction and refer you in the reference by name as the source of new information. Mean people and trolls will be ignored.



## System on the Chip (SOC)



### SOC Suppliers

There is no point to list any particular part numbers as they change every year, however it is important to keep a list of major suppliers of the SOC for Automotive market.



- NVidia (now also ARM)
- Texas Instruments
- Samsung
- Harman (daughter company of Sansung)
- Renesas
- Intel 
- Qualcomm
- and many more



## Image Signal Processor (ISP)

- demosaicing
- noise reduction
- auto exposure
- auto focus
- auto white balance



## Deep Neural Networks



### Data Parallelism

Dividing data and running it on multiple (TPU) cores running the same model. 



​	

## Pipeline Parallelism 

Pipeline Parallelism is dividing the model into segments running on different (TPU) cores.

















## Camera Perception



### Open Source Computer Vision Library (OpenCV)

OpenCV is a library that provides several hundreds of compute vision algorithms.

Below is a list of OpenCV modules, not all are supported by the target hardware you might be using:

- Core
- features2d
- flann
- imgcodecs
- imgproc
- ml
- objdetect
- photo
- shape
- stiching
- superres
- video
- videoio
- cudaarithm
- cudabgsegm
- cudacodec
- cudafeatures2d
- cudafilters
- cudaimgproc
- cudalegacy
- cudaobjdetect

- 



### FFmpeg

The FFmpeg stands for "Fast-forward MPEG".

The FFmpeg is a set of GNU open source software libraries for processing audio/video files and streams.

Some of the features:

- capture video from the camera
- save the video to the filesystem
- transcoding various media files into a common format
- editing
  - trimming
  - concatenation
- video scaling
- post-production effects
- standard complience
  - SMPTE
  - ITU





## OpenVX

The OpenVX is a open software standard "glue" layer for (embedded chip) hardware acceleration of perception software designed by Khronos Group.

The OpenXV makes application software running on top of OpenVX API to be hardware agnostic.



### OpenVX kernels

OpenVX kernels are software libraries that implement particular functionality.

Example of kernel wrappers provided by Texas Instruments on their SOC

DSP kernel wrappers:

- AbsDiff
- AccumulateSquare
- Accumulate
- AccumulateWeighted
- Add
- BitwiseAnd
- BitwiseNot
- BitwiseOr
- BitwiseXor
- Box3x3
- CannyEd
- ChannelCombine
- ChannelExtract
- ColorConvert
- ConvertDepth
- Convolve
- Dilate3x3
- EqHist
- Erode3x3
- Gaussian3x3
- HalfscaleGaussian
- HarrisCorners
- Histogram
- IntegralImage
- Lut
- Magnitude
- MeanStdDev
- Median3x3
- MinMaxLoc
- Multiply
- NonLinearFilter
- Phase
- Sobel3x3
- Subtract
- Threshold









## Color Edge Detection

An edge in the image is a sharp change in the color value. 

- the color images are usually converted to **grayscale** images first
- the Gaussian **blur**  is applied

Commonly it uses 3x3 pixel **Sobel** convolution filter.



# Resources

1. http://software-dl.ti.com/processor-sdk-linux/esd/docs/latest/linux/Foundational_Components_OpenVX.html

2. https://www.khronos.org/openvx/

3. https://www.youtube.com/watch?v=uihBwtPIBxM

4. https://en.wikipedia.org/wiki/Image_derivatives#Sobel_derivatives

5. https://en.wikipedia.org/wiki/FFmpeg

6. http://software-dl.ti.com/processor-sdk-linux/esd/docs/latest/linux/Foundational_Components_OpenCV.html

7. https://coral.ai/docs/edgetpu/pipeline/#overview

8. 

   



