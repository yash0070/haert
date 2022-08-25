Health Watcher
===================

Is an android Application that can estimate Heart rate, Blood pressure, Respiration rate and Oxygen rate from only the camera of the mobile without using any extra sensors. 


 I used the Fast Fourier transform code from here : https://github.com/danialgoodwin/android-app-contactless-vital-signs

 This used Bandpass filter and the Fast Fourier transform java files are inside the Math package.

This application uses the PPG signal which will be obtained from the mobile camera, only by applying image processing method on each frame to get the RGB intensities, each of them contains the PPG signal that will be processed to estimate the four vital signs. 

Our main goal from this project was to get good accuracy from the camera of the mobile compared to commercial devices.

The Application was tested on Sony Xperia Z2, the application problem that it is hardware dependent so it needs more testing. The Camera or the flash of each mobile can affect the reliability of the application, So the application should be modified to be more universal.
I used a sqlite local database for users’ privacy purposes, since critical information about the user must be entered to calculate the blood pressure like age, weight, height and gender.


How the processes works
-------------

A preview for 30 seconds of recording will be processed frame by frame to get the intensities of RBG colors on each frame.

(Heart rate)

Red and Green intensities will be stored in an array that will be applied on a Fast Fourier Transform, on the resultant array the highest peak after neglecting the noise which will be on the first few stored data will contain the frequency of the heart rate on 1 second, after that the heart beat will be estimated. (Fft)

----------

(Blood pressure)

After estimating the heart rate, blood pressure can be estimated by using some equation which will be mentioned in the references.

----------

(Respiration Rate)

Same as Heart Rate, the difference is a bandpass filter must be applied from 0.1 Hz to 0.4Hz with 0.2Hz center frequency to get the Respiration rate. (Fft2)

----------
(Oxygen Saturation Level)

Ac and Dc signals must be obtained from the PPG signal. Dc signal is the mean values of the Red and Blue intensities for the whole period of time, while the Ac Signal is the Standard Deviation and it can be calculated as follows from here : https://en.wikipedia.org/wiki/Standard_deviation 






References 
-------------

Oxygen Saturation Level (SPo2)
  
A. . K. Kanva, C. J. Sharma and S. Deb, "Determination of SpO2 and Heart-rate using Smartphone,International Conference on Control, Instrumentation, Energy & Communication, New Delhi, India, 2014.  

(Heart Rate & Respiration Rate)

EXTRACTING HEART RATE AND RESPIRATION RATE USING A CELL PHONE CAMERA
http://dreuarchive.cra.org/2013/Jimenez/documents/EXTRACTING%20HEART%20RATE%20AND%20RESPIRATION%20RATE%20USING%20A%20CELL%20PHONE%20CAMERA.pdf

(Blood Pressure)

MEASURING VITAL SIGNS USING SMART PHONES by B. Vikram Chandrasekaran.
https://pdfs.semanticscholar.org/7883/0cf36262f92049a7b4348813b3a7734f5287.pdf

(Image Processing)

https://software.intel.com/en-us/android/articles/trusted-tools-in-the-new-android-world-optimization-techniques-from-intel-sse-intrinsics-to




