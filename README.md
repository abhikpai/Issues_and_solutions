# Common_Issues_Resolved
This repo. does not contain any code!! But it contains common issues I faced while coding/running codes and their quick solutions which I found. Might be helpful for me or some one else in future.


## Issue 1:
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


## Issue 2:
```
ImportError: /lib/x86_64-linux-gnu/librsvg-2.so.2: undefined symbol: cairo_tag_end
```
* This issue is specific and  was found while executing a python import statement (@ https://github.com/bombardellif/hhi-stmrftracking) in Ubuntu 20.04 LTS*

* The strange thing here was, I was able to run the statement (without the above error) in Python3 console in the terminal with Python 3.8.2. But, I was not able to run the code in the anaconda environment with Python 3.7.6. 

#### How I Resolved:

* Upon investgation I found that the *librsvg-2.so* file was not present at the location *~/anaconda3/lib/* but was found at the location */lib/x86_64-linux-gnu/*. Updating the library to its 'suitable' version in anaconda is the workaround for the solution.

The following command as used:
```
conda install -c conda-forge/label/cf202003 librsvg
```
* This resulted in the creation of a new file "librsvg-2.so.2.40.19" at both the above locations. And the code ran fine.
