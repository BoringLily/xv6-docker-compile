# xv6-docker-compile
 A docker container that can build and run xv6-i386 with Qemu. 
 This container runs on M1 Mac via the Docker Desktop Architecture Emulator.

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

Make sure you still have the *"xv6_patched"* folder open inside vscode, if you do, run the following command:  

`docker run --name xv6_compile --platform linux/amd64 -ti -d -v $(pwd):/home/xv6 lilycute/xv6`

This command will install and setup the docker container and link it to the folder we currently have open in VScode,  
This means if you ever move the xv6 folder you will need to run this command to create a new container linked to the new folder location.

After running the command you can open the docker extension by clicking the whale log on the left side toolbar:  

<img width="40" alt="image" src="https://user-images.githubusercontent.com/53998902/187949554-cc221898-0d87-4b88-9161-b1888389d445.png">  

When you open that screen you will see the following:  

<img width="301" alt="image" src="https://user-images.githubusercontent.com/53998902/187949747-ee25ae6a-9cbc-47a1-ab9d-8f9b5e91e21a.png">

To complete the installation, right-click on the container  

<img width="298" alt="image" src="https://user-images.githubusercontent.com/53998902/187950126-de1b58b9-9aeb-4a1f-a790-c5e21030fe1c.png">

and then click *stop*  
![image](https://user-images.githubusercontent.com/53998902/187950442-7f086ee3-79e1-47e0-9c2c-f8993a5d2708.png)

You have now completed the installation and are ready to use the container to compile docker.

# How to run the container and compile xv6

Open VScode and open the xv6 source code folder.

Open the Docker Extension.

<img width="296" alt="image" src="https://user-images.githubusercontent.com/53998902/187951301-77eb5c4b-3383-403e-872a-3a2a4e501c12.png">

The red box on the container means that it is not running, to make it run, right-click on it and select *start*:  
<img width="304" alt="image" src="https://user-images.githubusercontent.com/53998902/187951745-23db82db-cd30-44e9-999a-27bcfb9be819.png">

When the container is running the red square will turn into a green triangle:  
<img width="303" alt="image" src="https://user-images.githubusercontent.com/53998902/187952061-1804816b-7259-4e12-a86d-3f9a7c1f6e34.png">

Once the container is running you can right-click on it and click on *Attach Shell*  
<img width="301" alt="image" src="https://user-images.githubusercontent.com/53998902/187954616-25e85e43-fd93-4451-901a-4b002e9cff23.png"> 

This will open a shell terminal that is inside the container environment. The docker container has your xv6 folder mounted to the home directory that means that any saved changes inside that folder will also update in the docker container. 

To compile your xv6, while inside the docker shell just run `make qemu-nox clean` this will compile the xv6 code and launche the qemu emulator to run the compiled image.

This is the terminal output when you run the above command:  
<img width="954" alt="image" src="https://user-images.githubusercontent.com/53998902/187957417-6510bb16-d3e3-46d9-9ac0-1a1994c179a2.png">

You are now running xv6. 

To exit the Qemu environment: Press CTRL+A and then Press X.
"CTRL+A" is a Qemu command shortcut and X is the exit command.

Whenever you are done with your code, you can keep the docker container running. 
If you wish to turn of the container while not in use, just navigate to the Docker extension, right click the container and click stop to shutdown the container. 

That is all there is to running the compiler docker container. Once you no-longer need the container, you can just click remove and then you can uninstall the docker app.

# Some random info:

If you ever get some error regarding docker, especially a connection error inside the vscode docker extension, make sure the Docker Desktop app is running.


