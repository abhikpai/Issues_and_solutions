# Solutions_to_some_issues
This repo. contains common issues I faced while coding/running codes and their quick solutions which I found. Might be helpful for me or some one else in future.


## Issue 1: Compilation of MPEGFLOW
```
usr/bin/ld: cannot find -l<nameOfTheLibrary>
```
>eg: /usr/bin/ld: cannot find -lavdevice

* This was a compilation issue while using "g++" in Ubuntu 20.04 LTS, which was encountered while building https://github.com/vadimkantorov/mpegflow


#### How I Resolved:

* First do a package search for "nameOfTheLibrary" :
```
apt-cache search <nameOfTheLibrary>
```
>eg: apt-cache search avdevice
  
 * Among the results, install the one which ends with "*-dev*"
 
>eg: apt-get install libavdevice-dev


## Issue 2: Python Import Error 
```
ImportError: /lib/x86_64-linux-gnu/librsvg-2.so.2: undefined symbol: cairo_tag_end
```
* This issue is specific and was found while executing a python import statement (@ https://github.com/bombardellif/hhi-stmrftracking) in Ubuntu 20.04 LTS

* The strange thing here was, I was able to run the statement (without the above error) in Python3 console in the terminal with Python 3.8.2. But, I was not able to run the code in the anaconda environment with Python 3.7.6. 

#### How I Resolved:

* Upon investgation I found that the *librsvg-2.so* file was not present at the location *~/anaconda3/lib/* but was found at the location */lib/x86_64-linux-gnu/*. Updating the library to its 'suitable' version in anaconda is the workaround for the solution.

The following command as used:
```
conda install -c conda-forge/label/cf202003 librsvg
```
* This resulted in the creation of a new file "librsvg-2.so.2.40.19" at both the above locations. And the code ran fine.


## Issue 3: Running MATLAB in Ubuntu (without using terminal commands)

* This is a simple issue where the executable MATLAB application is not visible in the dock panel, after installation of MATLAB.

* Usually, in such cases, you need to find the path where you have installed MATLAB. 

For me, MATLAB was installed at */usr/local/MATLAB/R2020a*. From here, you will need to locate the executable file for launching the MATLAB application.
In my case, it was located at */usr/local/MATLAB/R2020a/bin*.

Once you are at this location (through "cd */usr/local/MATLAB/R2020a/bin*" in terminal), execute the following command to launch MATLAB:
```
$ .\matlab
```

* You need to do this each time when you want to run MATLAB. Irritating right? Well, there is simple way out of it!

#### How I Resolved:

* Do the following in the terminal (Tested on Ubuntu only) : 
```
$ sudo apt install matlab-support
```

* This will launch a program which asks for the MATLAB installation path (*/usr/local/MATLAB/R2020a*). Use "TAB"-key to advance the cursor to "OK' button and hit "ENTER". Done!

* After this process, you will find a MATLAB icon in the dock panel.
