Recommender System Documentation
Hoo Fang Jie | 183002J

Project description
Analyze human behavior using eye-tracking technology and use a recommender system with the eye-tracker data to provide recommendations to the users.

Installations/packages used
Eye-tracker:
    • tobii_research
 GUI:
    • tkinter
Heatmap:
    • seaborn
    • matplotlib
    • Image from PIL
Others:
    • time
    • pandas

IMPORTANT: These codes are only usable with python versions 3.6 and below (the latest tobii_research package version is 3.6, hence it cannot be used with versions after 3.6)

Codes for refreshing heatmap (refresh.py)

File opens image, after 2 seconds opens the (translucent) GUI over the image. Eye-tracker data is appended into a list that will be used as data for the heatmap.  Heatmap is plotted on the canvas widget in the GUI. Canvas clears and replots the heatmap every 0.5 seconds automatically. After closing the GUI, the console will print a statement that states which part of the image was looked at the most. 

![image](https://github.com/hoofangjie1/FYP-Eyetracker/assets/128954974/c8b6460d-ea9e-4832-a174-d5018679df0c)
This opens the image in the device’s native photos app.

![image](https://github.com/hoofangjie1/FYP-Eyetracker/assets/128954974/6d8164e8-b741-473e-b420-006a7b453d80)
This detects the eye-tracker that is connected to the device.

![image](https://github.com/hoofangjie1/FYP-Eyetracker/assets/128954974/68728c29-6da2-43d8-8cb5-3b6d8c4d7c83)
This appends data (X and Y coordinates on the screen taken from the eye-tracker) from the “gaze” list and appends it to a sperate list “Cord”.

![image](https://github.com/hoofangjie1/FYP-Eyetracker/assets/128954974/61d8d794-ab43-444f-8b5c-803e52848bf2)
This runs the function “gaze_data_callback(i)” every time there is new gaze data.

![image](https://github.com/hoofangjie1/FYP-Eyetracker/assets/128954974/9c380c5d-497e-47a9-9f21-5ebb19560ab7)
Function “pplot()” plots the refreshing heatmap on the canvas

From the “Cord” list, the X and Y coordinates are split into lists “xCord” and “yCord” respectively, and any null values in those lists are cleaned.

![image](https://github.com/hoofangjie1/FYP-Eyetracker/assets/128954974/5ced40de-0014-4233-b593-aaa9c333c5f1)
The first 2 lines of code defines the heatmap and makes the chart fill the entire tkinter canvas.
The lines below plot the actual heatmap. X and Y limit are set to 0 and 1 as the maximum values of the eye-tracker coordinates are 0 and 1.

![image](https://github.com/hoofangjie1/FYP-Eyetracker/assets/128954974/27105bf4-c4ba-4881-8315-93ab4f15ba9d)
This clears the canvas and redraws it (canvas is a variable that was declared earlier). The canvas is then drawn into the GUI. The `root.after` loops the function “pplot” every 0.5 seconds.

![image](https://github.com/hoofangjie1/FYP-Eyetracker/assets/128954974/15136edf-099c-41e5-a8a3-eaa54b4c433a)
The function is then looped. The GUI opacity is lowered and the state of the GUI when opened will be initially full screen.

![image](https://github.com/hoofangjie1/FYP-Eyetracker/assets/128954974/b1856582-f690-499d-9553-5896532ae6d5)
This checks the “Cord” list for how many values are inside a certain range, and the amount of times its in those ranges, it adds 1 to the variable assigned to it. The variable is then appended to a list “rank”.

![image](https://github.com/hoofangjie1/FYP-Eyetracker/assets/128954974/64f22523-9b34-451f-b6bf-db8731240122)
This checks to see which variable appended into the “rank” list has the highest value, and then prints a statement depending on which variable has the highest value.

Codes for Use Case (usecase.py)

When the python file is run, an image of 4 food items will open in the native photos app. After 5 seconds of gathering gaze data, a heatmap of the coordinates will be plot over the photo of the food image on the GUI, and there is a label at the bottom that states which food you were looking at the most, and give some recommendations for what food the recommender thinks you might like.






