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
