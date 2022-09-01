# xv6-docker-compile
 A docker container that can build and run xv6-i386 with Qemu, the docker container runs on M1 mac

# How To Setup
**NOTE: theses instructions are based of the installation process on M1 MacOS as this is the primary usecase for the container** 

## STEP 1

1. [Docker Desktop](https://www.docker.com/products/docker-desktop/)
2. [Visual Studio Code](https://code.visualstudio.com/)

First you must install the above applications, follow the respective installer instructions.
When installing Docker Desktop, you can skip the tutorial prompt as it is not relevant to this installation.

## STEP 1.5

This process assumes you have xv6 source code installed.
If you do not, you can install the file "xv6_patched.tar.gz" from this repository.

To download the file. Click on the file:
![image](https://user-images.githubusercontent.com/53998902/187934692-9229d28a-f834-4c33-a93f-ee783140b576.png)

On the next page click "Download"
<img width="1287" alt="image" src="https://user-images.githubusercontent.com/53998902/187935412-dc2787c6-841a-4ff5-9749-37ec21ff0a59.png">

Once the file is downloaded navigate to your computers donwloads folder and double-click file "xv6_patched.tar.gz".
This will unzip the file and create a folder "xv6_patched". Move this folder to a place that would be convenient for you as this is your xv6-i386 source code that you can edit.

If you have this source Code installed please proceed to STEP 2

## STEP 2

Launch up the Docker Desktop app and then you can minimize it as we won't need the UI Dashboard.

Launch Visual Studio Code, Click on *File* (in the top left corner) and then click on *Open Folder* 
then find and open the *"xv6_patched"* folder.

This will open the folder in VScode.

On your left side is going to be the file explorer that shows all the files and folders in the *"xv6_patched"* directory.  
Find and click on the *Makefile*.  
In the opened *Makefile* find line number 56 that contains the text `#QEMU :=`  
and replace the code in that line with `QEMU := qemu-system-i386`


## STEP 3 

In the left-side toolbar inside VSCode click on the extensions button.  

<img width="46" alt="image" src="https://user-images.githubusercontent.com/53998902/187940058-2a116351-7c27-4335-890a-a7f3b7c81bdf.png">  

In the search-bar type "Docker" and install the following extention:  

<img width="299" alt="image" src="https://user-images.githubusercontent.com/53998902/187940589-1888d2a8-da59-477f-b143-cd0200046b28.png">

Once the extension is installed it should appear in the tool-bar like so:  
  
<img width="49" alt="image" src="https://user-images.githubusercontent.com/53998902/187940857-8d55da05-3962-4697-adcc-db6997bd8451.png">

## STEP 4 

In VScode navigate to the toolbar at the top of your screen and click on *Terminal -> New Terminal* 

This will open a terminal tab at the bottom of the screen in VScode.








