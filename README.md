# Zenith
This repository is merely to show my automation I made for work, however I cannot share the code as it has somewhat sensitive info. That being said, lets learn more about it

## What it does:

Much of what it does is based on screen image identifier and locator, it takes a screenshot of the screen(s) and does a quick comparation to try and find said window/button/etc on screen, this is done with the help of the very useful EmguCV
Once the control has been identified, it will immediately move the mouse to where it is, the inputs for mouse clicks, keyboard presses and types, are handled by the InputSimulator library, and are in the "MouseHandler" class, that as the name suggests,
handles anything related to the mouse: clicks, moving, events, etc.

Speaking of, we can't just blindly handle stuff on screen and immediately click on it right? that would cause some scary bugs and unwanted functions, which is why there is two barriers for that, first one is the DetectMouseStates() function, since we are working with the company's program that is in an RDP, the mouse states vary wildly each time you open it, which is why everytime my tool is started and ran, it will bring the RDP to front and begin to move the mouse to the corners of windows and text boxes, this will change the cursor to various other icons like for example the arrows for resizing a window. These icons hold some sort of numeric value which we can use to track whether something is being done or not, since in the cases where something is being done, your cursor will change to the default "Loading" cursor state (the spinning glowing wheel) my "Delay()" function handles that by checking if the mouse's current value state matches any of the "non loading" states it has saved before starting, and if it doesn't match, it waits for it to change before moving on, this Delay() function is called after almost every step to improve accuraccy. 

It also has built in functions to convert CSVs to Excel, and also convert Excel to PDF, this is what it uses to generate our daily "Pallet Putaway Report" a pdf is generated programmatically with everything our team needs in the report, which in this case is the container, pallet and location.

## Video samples (TBD):
