### Adjusted OpenCV for Hololens UWP build  

Build tested on Windows 10.0.14986 (AMD64) with VS2015 Community Edition

For convenience I'm including 'Release' binaries in \opencv-hololens\release_binaries.7z
but I'm not going to update it. So it is preferable to work out the build yourself if you want to sync up with main opencv trunk.

Following prgs installed:

- cmake => https://cmake.org/ (tested with 3.6.2)
- python2.7 => https://www.python.org/download/releases/2.7/

How to run the build:

1/ download or clone 
- opencv-hololens (https://github.com/sylvain-prevost/opencv-hololens) 
- opencv-hololens-contrib (https://github.com/sylvain-prevost/opencv_contrib-hololens)

worry-free structure:          
- parent_dir\opencv-hololens-contrib
- parent_dir\opencv-hololens

(you neeed to adjust the opencv-hololens\build_hololens_uwp.bat batch file if using a diff structure)


2/ run parent_dir\opencv-hololens\build_hololens_uwp.bat

3/ open parent_dir\opencv-hololens\bin\WS\10.0\x86\OpenCV.sln

4/ Select Platform : Win32

5/ Select Configuration (either Debug or Release)

6/ find all binaries in opencv-hololens\bin\WS\10.0\x86\[Configuration]

7/ You can now add references to the generated binaries in your Hololens C++ UWP application(s) either via .dll & .lib, or using the .winmd


Note1: 
If using C#, you've got to create a "Window Runtime Component" wrapping library to access the native UWP OpenCV.
This is what OpenCvSharp provides, however to date, it does not support UWP for hololens.
To not have to re-create everything, I suggest to simply expose the strict minimum from the WRC library and limit large buffer exchanges 
between .Net layer and WRC layer to strict minimum.

Note2:
I'm not pushing the changes in the main opencv trunk mainly because I'm not familiar with their commit rules, and because I'm pretty sure
 that the 'adjustements' I did are not acceptable as is. 




