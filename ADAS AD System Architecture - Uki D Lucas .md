# ADAS and Autonomous Driving System Architecture



Last edited on August 27, 2021

by Uki D. Lucas
https://www.linkedin.com/in/ukidlucas/



## Motivation

Many startups prototype their ideas on Linux general-purpose computers (laptops, Nvidia Xavier) to realize, months or years later, that their **prototype has no chance of running in a low-cost, hardware-accelerated, safety-oriented, embedded system** without a major code decoupling and a general re-write. The right design from the ground up is the key.

Engineers who switch to the field of **Advanced Driver Assistance Systems (ADAS)** and **Automated Driving (AD)** usually have a rich set of skills, but generally lack the specific to this field **System Architecture** perspective. 

This situation may change in the next few years as companies like Tesla keep publicizing their designs (see reference #1), but today such designs remain somewhat esoteric. 

This text attempts to be a practical guide while referencing **publicly available information** in the reference section at the end.

## Contributions by the readers

The architects are a very opinionated bunch, every company has different approach to the design, so I expect a metric ton of criticism. 

Please consider the following: if you provide me a correction in a constructive format such as "You have written that X is Y, but based on [URL included] the X is really Z" than I will include the correction and refer to you in the reference by name as the source of new information. Mean people will be ignored.

## Contact the Author

If you are reading this book, I would love if you **connected with me to collaborate on the future updates**:
https://www.linkedin.com/in/ukidlucas/



## Value provided

In order to write this book I had to sacrifice many weekends and burn some midnight oil. 

The field of automated driving is changing constantly and updating the book takes effort and motivation. 

In fact, more papers are published daily on the subject of perception than any single human could read.

The author assumes there will be very limited group of people who are interested in reading this book, so every copy sold will make the motivational difference in order to continue the effort.

This book is sold with license for a single person who paid for it. Sharing any part of the content is a violation of a copyright and an ethical trespass. 

If you would like to buy this book to share it with your team as PDF or ebook, please contact the author for a deep group discounts.  

This book costs a fraction of what a System Architect makes in one hour.

If you have obtained a free copy of this book please consider purchasing  a copy from Amazon Kindle to show your support for author's efforts. 



# Updates

I hope you will find this book a good reference. 

If you previously purchased the book on Kindle, I suggest to occasionally delete it from your device and download it again to get the newest version. The date at the beginning should be an indicator.







## What is function of a System Architect?

The System Architect's job is to ensure that the parts of the system, including hardware, peripherals, software, Human-Machine Interfaces (HMI), remote services, as well manufacturing, **delivers a product that functions well as a whole**. The System Architect may not know the details of implementation of a particular component, but should investigate if that component would function well in the final product. The System Architect usually analyses data flows, creates high-level interaction diagrams and system requirements specifications (SRS) from which the user experience (UX) experts, mechanical, electronic and software architects can design their particular domains.



## Feature-level components of ADAS/AD

There are many subsystems that comprise of ADAS/AD domain. 

Here are some of the examples of features listed from most common to futuristic:

- Surround View (SV)
- Augmented Reality with a console display or windshield-projected heads-up display (HUD) 
- Rear eMirror, Camera Monitoring System (CMS)
- Side eMirrors, Camera Monitoring System (CMS)
- Lane Keep Assist (LKA)
- Pedestrian and large animal detection (perception component)
- Obstacle detection (perception component)
- Emergency Breaking System (EBS)
- Cross-Traffic Alert (CTA)
- Curb Detection (perception component)
- Street-sign detection (perception component)
- Free-Space Detection (perception component)
- Automated Cruise Control (ACC)
- Driver Monitoring System (DMS)
- Occupant Monitoring System (OMS)
- Automated Park Assist (APA)
- Automated Valet Parking (AVP)
- Valet parking - remote summon 
- L2 automated highway driving, driver hands on the steering wheel
- L3 any road autonomy, driver supervision required
- L4 any road autonomy, driver controls provided, driver supervision not required
- L5 full autonomy, no driver controls provided

As you can see the field is very large and constantly growing, this field is a true bonanza for a motivated engineer.



## Design Assumptions



The traditional approach of auto manufacturers, or as they are called in the industry, original equipment manufacturers (OEM), is to provide a **low-cost electronic control unit (ECU) per each feature**. This is to done to enable and insulate model year-to-year upgrades, offer multiple vehicle price-level offerings and use different suppliers.

The recent tendency in the market is to combine many of these into more powerful Domain Controller that host multiple features which are **designed based on the safety level desired**. 

The manufacturers start realizing that **users expect frequent over-the-air (OTA) software upgrades **, which is easier with a single unit. 

It is easier to find place for a single domain controller than 10 different ECUs. 

It is cheaper to manufacture a single unit. 

A single unit draws less current. 

It is also easier to design the cooling which is a big factor in automotive.

In this book I will explore a **Domain Controller that meets safety levels up to L2 of autonomy** and then analyze the design of **L3+ based on the Tesla design** as that is the only one that is publicly available at this time.



## Tools of the System Architect

In this book, I will use Omnigraffle software to draw the diagrams. The book is written in a simple markdown (MD) format using Typora editor. I also use GitHub extensively to store my projects.

In smaller organizations, for keeping track of **linkage between documentation, requirements and tasks** (project management), the combination of **Atlassian JIRA and Confluence**  are quite sufficient and can be easily obtained for total of $120 per month for organizations up to 20,000 people. (see reference #8)

Atlassian tools are well proven in the industry and generally do not require any introduction. With a bit of planning and learning, you can show the **required traceability, and baseline** documentation for future **ASIL audits**.

The big organization, on the other hand, love to make people's life a nightmare. They also tend to create a lot of useless jobs that sip the living spirit of everyone's around and increase the overhead costs.

In the industry, the **Enterprise Architect** is commonly used. I know all software is gradually improving, but as of the time of writing the user experience is terrible (circa late 1990s), integration with requirements is awful and uni-directional and licenses so expensive that most of the developers never get access to it, or they get "floating license" which is equivalent of a crew of workers digging a ditch with one shovel.  

Much of the documentation and requirements management is done in Polarion (better) or in IBM ALM (aka doors), I had displeasure of working daily over 4 and a half years with the last one. 

There is a big opportunity for modern software companies to provide integrated environment for **versioning and traceability between requirements, design documents, epics, features and tasks and code commits**.



## Traceability throughout the development lifecycle 



















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

8. [Atlassian Confluence](https://confluence.atlassian.com/)

9. [Automotive Safety Integrity Level ISO 26262) - Functional Safety for Road Vehicles standard](https://en.wikipedia.org/wiki/Automotive_Safety_Integrity_Level)

10. 

    



