# Common_Issues_Resolved
This repo. does not contain any code!! But it contains common issues I faced while coding/running codes and their quick solutions which I found. Might be helpful for me or some one else in future.


## Issue 1:
```
usr/bin/ld: cannot find -l<nameOfTheLibrary>
```
>eg: /usr/bin/ld: cannot find -lavdevice

* A compilation issue while using "g++" in Ubuntu 20.04 LTS, which was encountered while building https://github.com/vadimkantorov/mpegflow


#### How I Resolved:

First do a package search for "nameOfTheLibrary" :
```
apt-cache search <nameOfTheLibrary>
```
>eg: apt-cache search avdevice
  
 Among the results, install the one which ends with "*-dev*"
 
>eg: apt-get install libavdevice-dev


## Issue 2:
```
ImportError: /lib/x86_64-linux-gnu/librsvg-2.so.2: undefined symbol: cairo_tag_end
```
* This issue is specific and  was found while executing a python import statement (@ https://github.com/bombardellif/hhi-stmrftracking) in Ubuntu 20.04 LTS*

The strange thing here was, I was able to run the statement (without the above error) in Python3 console in the terminal with Python 3.8.2. But, I was not able to run the code in the anaconda environment with Python 3.7.6. 

#### How I Resolved:

* Upon investgation I found a workaound for the issue i.e, update the library to its 'suitable' version in anaconda. 
The following command as used:
```
conda install -c conda-forge/label/cf202003 librsvg
```
