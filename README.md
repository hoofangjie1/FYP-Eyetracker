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

Codes for refreshing heatmap

File opens image, after 2 seconds opens the (translucent) GUI over the image. Eye-tracker data is appended into a list that will be used as data for the heatmap.  Heatmap is plotted on the canvas widget in the GUI. Canvas clears and replots the heatmap every 0.5 seconds automatically. After closing the GUI, the console will print a statement that states which part of the image was looked at the most. 


This opens the image in the device’s native photos app.


This detects the eye-tracker that is connected to the device.


This appends data (X and Y coordinates on the screen taken from the eye-tracker) from the “gaze” list and appends it to a sperate list “Cord”.


This runs the function “gaze_data_callback(i)” every time there is new gaze data.


Function “pplot()” plots the refreshing heatmap on the canvas

From the “Cord” list, the X and Y coordinates are split into lists “xCord” and “yCord” respectively, and any null values in those lists are cleaned.


The first 2 lines of code defines the heatmap and makes the chart fill the entire tkinter canvas.
The lines below plot the actual heatmap. X and Y limit are set to 0 and 1 as the maximum values of the eye-tracker coordinates are 0 and 1.
 

This clears the canvas and redraws it (canvas is a variable that was declared earlier). The canvas is then drawn into the GUI. The `root.after` loops the function “pplot” every 0.5 seconds.


The function is then looped. The GUI opacity is lowered and the state of the GUI when opened will be initially full screen.


This checks the “Cord” list for how many values are inside a certain range, and the amount of times its in those ranges, it adds 1 to the variable assigned to it. The variable is then appended to a list “rank”.



This checks to see which variable appended into the “rank” list has the highest value, and then prints a statement depending on which variable has the highest value.

Codes for Use Case

When the python file is run, an image of 4 food items will open in the native photos app. After 5 seconds of gathering gaze data, a heatmap of the coordinates will be plot over the photo of the food image on the GUI, and there is a label at the bottom that states which food you were looking at the most, and give some recommendations for what food the recommender thinks you might like.


Columns in the food.csv file



Recommender is a content-based recommender from the “Hands-on recommendation systems with python” book by Rounak Banik.
Function “content_recommender” takes in a value (name of a local food) and returns a string of the 5 local food that are most similar to the input value.


Opens the image of the 4 local foods in device’s native photos app.


This detects the eye-tracker that is connected to the device.


This appends data (X and Y coordinates on the screen taken from the eye-tracker) from the “gaze” list and appends it to a sperate list “Cord”.


This runs the function “gaze_data_callback(i)” every time there is new gaze data.


From the “Cord” list, the X and Y coordinates are split into lists “xCord” and “yCord” respectively.


Function “cplot()” creates the heatmap using eye-tracker data collected in the past 5 seconds. The initial image of the 4 local foods that was opened at the start of running this file is used as the background image in the canvas. 


Defining the heatmap dimensions.


This plots the heatmap using the X and Y coordinates data, while lowering opacity so that the background image (of the 4 local foods) can be seen. `test.collections[0].set_alpha(0)` makes the heatmap without any datapoints transparent, and then the background image is placed in the canvas.


This checks the “Cord” list for how many values are inside a certain range, and the amount of times it’s in those ranges, it adds 1 to the variable assigned to it. The variable is then appended to a list “rank”.


This changes the value of the variable “most_looked” to the variable with the highest value in the list “rank”. The variable “most_looked” is then used as a parameter of the “content_recommender” function.


This label is a string that shows which food you looked at and what foods are similar to them.
Challenges faced
Refreshing heatmap:
Some issues I had while creating this was trying to make the heatmap refresh smoothly. My first method was to use the image that currently opens first as the background image of the canvas, and then plot the heatmap over it (and lower its opacity so you can see both the heatmap and background image). 
To refresh the canvas, the background image also must be cleared away and then plotted again along with the heatmap, making the GUI flicker every time it refreshes.

My solution was to remove the background image completely and have it open at the start in a native photo app on the device, then run the GUI with low opacity. This allowed me to achieve what I wanted to do while also making the code run smoother (as the background image didn’t need to be cleared and replotted). 

Use case:
I did not have much difficulty with the use case compared to the previous refreshing heatmap, the only difference was the addition of the recommender system. I had to make a new CSV file with local food data from scratch which was a bit tedious.

I had another issue regarding the background image. The origin (0,0) from the eye-tracker is on the top-left of the screen, whereas the origin of heatmap is bottom-left. To solve this issue, I had to invert the Y-axis, and then set the origin of the background image to “lower” so that the image is not upside down. And to resize the image, I set the aspect to “auto”.
