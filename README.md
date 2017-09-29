# **Finding Lane Lines on the Road** 
<img src="laneLines_thirdPass.jpg" width="480" alt="Combined Image" />

When we drive, we use our eyes to decide where to go. The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm. In this project,  I use Python and OpenCV to detect lane lines in images. 

# What I did
This is the first project of the udacity self-driving car engineer nanodegree. The pipeline is in P1.ipynb. In the project, our objective is to using some computer vision methods to detect lane lines in videos. The expected result will looks like P1_example.mp4. 

To detect lane lines in a video is actually to detect lane lines in series of pictures. Here I will simply discuss about the pipeline I use to complete this task:

(1) Transform the image to grayscale;

(2) Conduct a gaussian blur on the grayscale image to reduce the noise;

(3) Conduct canny edge detection (parameters: low_threshold and high_threshold). The algorithm will first detect strong edge (strong gradient) pixels above the high_threshold, and reject pixels below the low_threshold. Next, pixels with values between the low_threshold and high_threshold will be included as long as they are connected to strong edge; 

(4) Use a four sided polygon mask to filter the image. We do this to simplify the task because the lane lines will always be in some range of the pictures. This step also can be done early; 

(5) Run hough transformation to find the lane lines; 

(6) Draw the lane lines on the picture. We should be careful in this step because there are many lines that are actually lane lines. Here we filter all line segments by the slopes and the difference to the median of all segments. 

I did not finish the optional challenge. It will be solved here: https://github.com/Gan-Jiang/Self-Driving-P4-Advanced-Lane-Lines. 

# Dependencies. 
**Step 1:** Getting setup with Python

To do this project, you will need Python 3 along with the numpy, matplotlib, and OpenCV libraries, as well as Jupyter Notebook installed. 

We recommend downloading and installing the Anaconda Python 3 distribution from Continuum Analytics because it comes prepackaged with many of the Python dependencies you will need for this and future projects, makes it easy to install OpenCV, and includes Jupyter Notebook.  Beyond that, it is one of the most common Python distributions used in data analytics and machine learning, so a great choice if you're getting started in the field.

Choose the appropriate Python 3 Anaconda install package for your operating system <A HREF="https://www.continuum.io/downloads" target="_blank">here</A>.   Download and install the package.

If you already have Anaconda for Python 2 installed, you can create a separate environment for Python 3 and all the appropriate dependencies with the following command:

`>  conda create --name=yourNewEnvironment python=3 anaconda`

`>  source activate yourNewEnvironment`

**Step 2:** Installing OpenCV

Once you have Anaconda installed, first double check you are in your Python 3 environment:

`>python`    
`Python 3.5.2 |Anaconda 4.1.1 (x86_64)| (default, Jul  2 2016, 17:52:12)`  
`[GCC 4.2.1 Compatible Apple LLVM 4.2 (clang-425.0.28)] on darwin`  
`Type "help", "copyright", "credits" or "license" for more information.`  
`>>>`   
(Ctrl-d to exit Python)

run the following commands at the terminal prompt to get OpenCV:

`> pip install pillow`
`> conda install -c https://conda.anaconda.org/menpo opencv3`

then to test if OpenCV is installed correctly:

`> python`  
`>>> import cv2`  
`>>>`  
(Ctrl-d to exit Python)

**Step 3:** Installing moviepy  

We recommend the "moviepy" package for processing video in this project (though you're welcome to use other packages if you prefer).  

To install moviepy run:

`>pip install moviepy`  

and check that the install worked:

`>python`  
`>>>import moviepy`  
`>>>`  
(Ctrl-d to exit Python)

**Step 4:** Opening the code in a Jupyter Notebook

You will complete this project in a Jupyter notebook.  If you are unfamiliar with Jupyter Notebooks, check out <A HREF="https://jupyter-notebook-beginner-guide.readthedocs.io/en/latest/" target="_blank">this link</A> to get started.

Jupyter is an ipython notebook where you can run blocks of code and see results interactively.  All the code for this project is contained in a Jupyter notebook. To start Jupyter in your browser, run the following command at the terminal prompt (be sure you're in your Python 3 environment!):

`> jupyter notebook`

A browser window will appear showing the contents of the current directory.  Click on the file called "P1.ipynb".  Another browser window will appear displaying the notebook.  Follow the instructions in the notebook to complete the project.  
