# Common_Issues_Resolved
This repo. does not contain any code!! But it contains common issues I faced while coding/running codes and their quick solutions which I found. Might be helpful for me or some one else in future.


## Issue 1:
```
usr/bin/ld: cannot find -l<nameOfTheLibrary>
```
>eg: /usr/bin/ld: cannot find -lavdevice

**A compilation issue while using g++ which was encountered while building https://github.com/vadimkantorov/mpegflow
OS: Ubuntu 20.04 LTS**

#### How I Resolved:

First do a package search for <nameOfTheLibrary>
```
apt-cache search <nameOfTheLibrary>
```
>eg: apt-cache search avdevice
  
 Among the results, install the one which ends with "*-dev*"
 
>eg: apt-get install libavdevice-dev
