# Jetson_nano_Kinect2

These are the steps I took to get the Kinect2 to run on  jetson nano.
These steps will let you run the Kinect2 in C++ and Python.

you need to have youre nano setup with instructions from this repo:
https://github.com/valdivj/jetson-nano-yolov2-darkflow

You need to make sure that you have installed Opencv 4.1.
There is a bug in opencv 4.0 that makes the Kinect2 angry.

To get started head on over to: https://github.com/OpenKinect/libfreenect2
This is the Libfreenect2 repo.
We will need to install this first before we can install Pylibfreenect2.
Scroll down to the LINUX install section and start there:

You need to replace "/joev/" with youre path name.

These are the commands I used:

1.$git clone https://github.com/OpenKinect/libfreenect2.git

2.$cd libfreenect2

3.$sudo apt-get install build-essential cmake pkg-config

4.$sudo apt-get install libusb-1.0-0-dev

5.$sudo apt-get install libturbojpeg0-dev

6.$sudo apt-get install libglfw3-dev

7.$sudo apt-get install libopenni2-dev

8.$mkdir build

9.$cd build

10.$cmake .. -DCMAKE_INSTALL_PREFIX=$HOME/freenect2

11.$make

12.$make install

13.$sudo cp ../platform/linux/udev/90-kinect2.rules /etc/udev/rules.d/

14.$cd /home/joev/libfreenect2/build

To test that everything works run:sudo ./bin/Protonect.
You should get a video and depth streams.
This install was preaty straight forward.

# Now to install Plibfreenect2 so we can run Kinect2 in python

head over to :https://github.com/r9y9/pylibfreenect2

You need to replace "/joev/" with youre path name.

1. $sudo ~/.bashrc

2. Scroll down to the bottom and install this:
export LIBFREENECT2_INSTALL_PREFIX=/home/joev/libfreenect2/
export LD_LIBRARY_PATH=/home/joev/freenect2/lib:$LD_LIBRARY_PATH

3. ctrl x then enter yes then enter.

4. $source ~/.bashrc

5. Copy "config.h" & "export.h" from /home/joev/libfreenect2/build/libfreenect2/
and install them in:
/home/joev/libfreenect2/include/libfeenect2/

6. to test run:
${LIBFREENECT2_INSTALL_PREFIX}include/libfreenect2/config.h
if everything is in right place it will return:
bash: /home/joev/libfreenect2/include/libfreenect2/config.h:permission denied

7. copy "lib" folder from :/home/joev/libfreenect2/build/
and put in:
/home/joev/libfreenect2/ 

8. Go ahead and start youre .virtual enviroment.

9.$pip install pylibfreenect2

10.$pip install git+https://github.com/r9r9/pylibfreenect2

11.$git clone https://github.com/r9r9/pylibfreenect2.git

12.$cd /home/joev/pyliqbfreenect2/examples

13.$python selective_stream.py

14.Damn

You should be getting the video streams if everything went well.




