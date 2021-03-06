# Lesson 07 - events and linear interpolation

In this lesson we'll be learning about these new concepts:

* [Events](https://en.wikipedia.org/wiki/Event-driven_programming)
* [Linear interpolation](https://en.wikipedia.org/wiki/Linear_interpolation) more commonly known as *lerp*

## Review

In the previous lesson we continued working on the *baseball toss* program by adding an alien that tosses baseballs using computer animation code. To do this we needed to learn some new programming concepts, including:

* [Arithmetic](https://en.wikipedia.org/wiki/Arithmetic)
  * *Math* code blocks
    * arithmetic  
        ![00-040-020](../images/00-040-020.math.arithmetic.jpg)  
        **figure 00-040-020** "Arithmetic" value code block form the Math tray
* [Conditions](https://en.wikipedia.org/wiki/Conditional_(computer_programming))
  * *Logic* code blocks
    * if do  
        ![00-030-010](../images/00-030-010.logic.ifdo.jpg)  
        **figure 00-030-010** "If do" condition code block from the Logic tray
    * compare  
        ![00-030-030](../images/00-030-030.logic.compare.jpg)  
        **figure 00-030-030** "Compare" expression code block from the Logic tray
* [Loops](https://www.cs.utah.edu/~germain/PPS/Topics/loops.html)
  * *Control* code blocks
    * Every do  
        ![00-020-010](../images/00-020-010.control.everydo.jpg)  
        **figure 00-020-010** "Every do" loop code block from the Control tray
* [Variables](https://www.cs.utah.edu/~germain/PPS/Topics/variables.html)
  * *Variable* code blocks
    * number  
        ![00-050-010](../images/00-050-010.variables.number.jpg)  
        **figure 00-050-010** "Number" value code block from the Variables tray
    * get variable  
        ![00-050-050](../images/00-050-050.variables.getvariable.jpg)  
        **figure 00-050-050** "Get variable" value code block from the Variables tray
    * set variable  
        ![00-050-040](../images/00-050-040.variables.setvariable.jpg)  
        **figure 00-050-040** "Set variable" method code block from the Variables tray
* [Objects](https://en.wikipedia.org/wiki/Object-oriented_programming)
  * *Part* code blocks
    * Sticker  
      ![00-500-100](../images/00-500-100.parts.sticker.jpg)  
      **figure 00-500-100** "Sticker" part from "Add Parts"
      * move to  
        ![00-500-170](../images/00-500-170.parts.sticker.moveto.jpg)  
        **figure 00-500-170** "Move to" method on "Sticker" part
* [Animation](https://en.wikipedia.org/wiki/Computer_animation)

## Challenges

Before we start coding, we need to learn about events and linear interpolation (lerp) by completing these challenges:

* [Challenges > Events > Create a Paintbrush](https://code.kano.me/challenge/CLUB04/CLUB04_01_paint)
* [Challenges > Animation > Learning to Lerp](https://code.kano.me/challenge/CLUB012/CLUB012_01_lerp)

## Hands on

In this hands on exercise, we'll make more improvements to the *baseball toss* program. Right now our alien tosses baseballs over and over again to the same spot. Kind of boring huh? Wouldn't it be cool if we could add some code to make the alien toss baseballs to different places on the canvas?

1. Remix the last version of the *baseball toss* creation you shared. If you can't find it, don't worry, just import it from [baseball-toss-remix-1.kcode](../06-loops-and-variables/baseball-toss-remix-1.kcode) in the previous lesson.
1. Move all of the code blocks after the "Draw: stamp sun smiling" and park them to the side. We will use some of them later.
1. Add some instructions to the bottom of the canvas so people know how to use your program.
    1. Add a new *Text* part.
    1. Drag a new "Text: value 'Text'" code block from the Text tray and connect it to the bottom of the "Draw: stamp Sun smiling" code block.
    1. Change the value "Text" to "Click where you want the alien to toss the baseball"
    1. Drag a new "Text: move to x y" code block from the Text tray and connect it to the bottom of the previous code block. Change the coordinates to x = 400, y= 580.  
        ![07-010](./images/07-010.jpg)  
        **figure 07-010** New help text
1. Add two new variables named "alienx" and "alieny" that we can use to control where the alien gets drawn. This will make it easy to move the alien later, or to find the current position of the alien when the baseball gets tossed.
    1. Set "alienx" to 100.
    1. Set "alieny" to 400.  
        ![07-020](./images/07-020.jpg)  
        **figure 07-020** New variables
1. Find the "Draw: move to" and "Draw: stamp Alien" code blocks you parked and attach them to the previous code bock. Set the x and y coordinates of the "Draw: move to" code block to the "alienx" and "alieny" variables.  
    ![07-030](./images/07-030.jpg)  
    **figure 07-030** Use variables to draw the Alien
1. Find the  "Sticker: image Baseball" and "Sticker: set size to scale 25" code blocks you parked and attach them to the previous code block.
    1. Rename the "Sticker" part to "Baseball" by changing the name in the "Add Parts" section. This will make your code more readable.  
        ![07-040](./images/07-040.jpg)  
        **figure 07-040** Rename the Sticker part to "Baseball"
1. Find the "Set baseballx to 200" code block you parked and attach it to the previous code block.
    1. Rename "baseballx" to "baseballnowx" by clicking the dropdown arrow and choosing "Rename variable". We are going to be adding a lot more variables and this will make your code more readable. This variable will track the current x coordinate of the baseball.
    1. Set the value of "baseballnowx" to the variable "alienx". This will ensure that the baseball toss always starts from the same x coordinate where the alien was drawn.  
        ![07-050](./images/07-050.jpg)  
        **figure 07-050** Modify "baseballx" variable
1. Create three new variables we will use to track the starting and ending coordinates of the baseball toss.
    1. Add a variable "baseballnowy" and set it to "alieny". This variable will track the current y coordinate of the baseball.
    1. Add a variable "baseballendx" and set it to "800". This variable will be used to set the x coordinate of where the baseball is tossed. We'll set it to 800 initially because we have to start tossing the baseball somewhere.
    1. Add a variable "baseballendy" and set it to "alieny". This variable will be used to set the y coordinate of where the baseball is tossed. We'll set it to be the same as the variable "alieny" initially because we have to start tossing the baseball somewhere.  
        ![07-060](./images/07-060.jpg)  
        **figure 07-060** New variables
1. Create a new variable named "lerppct" and set it to "0". We will use this later inside the loop when we're moving the baseball sticker using the "lerp from" code block.  
    ![07-070](./images/07-070.jpg)  
    **figure 07-070** New "lerpct" variable
1. Find the "Every 1 milliseconds" loop you parked and attach it to the previous code block. *Important*: Drag all the code blocks inside of it back off to the right and park them to the side so you can use them later.  
    ![07-080](./images/07-080.jpg)  
    **figure 07-080** Every 1 milliseconds loop with extra code parked to the side
1. We need to add some code to reset the "lerppct" variable to 0 inside the loop. The "lerppct" variable is a percentage that will change from 0 to 100. When the baseball toss starts the "lerppct" will be 0, then halfway through the baseball toss the "lerppct" will be 50, then at the end of the baseball toss "lerppct" will be 100. If "lerpct" is greater than 100 we need to reset it back to 0 for a new baseball toss.
    1. Drag a new "if do" code block from the Logic tray and connect it inside the "Every 1 milliseconds" loop.
    1. Drag a new "compare" code block from the Logic tray and connect it to the right of the "if" on the previous code block.
        1. Set the first value to the "lerppct" variable. This is the first value that will be evaluated in the comparison expression.
        1. Change the comparison operator from "=" to ">" which means "greater than". This sets the type of comparison to be performed in the comparison expression.
        1. Set the second value to "100". This is the second value that will be evaluated in the comparison expression. So if the comparison expression evaluates to "true" then the code in the "do" section gets run.
    1. Drag a new "set variable" code block from the variables tray and connect it to the bottom of "if". Change "item" to "lerppct" and set the value to 0. This code only runs if the comparison expression evaluates to "true" which means we need to rest "lerppct".  
    ![07-090](./images/07-090.jpg)  
    **figure 07-090** Reset the "lerppct" variable when it's greater than 100
1. Find the "Baseball: move to x y" code block you parked and attach it to the bottom of the "if do" code block but still inside the "Every 1 milliseconds" loop. Change the y coordinate from 400 to the variable "baseballnowy". You can go ahead and throw the rest of the code blocks you have parked to the right in the trash, you won't be needing them.  
    ![07-100](./images/07-100.jpg)  
    **figure 07-100** Add "Baseball: move to" back into the loop
1. Now we need to add some code at the end of the loop that adjusts the values of the "baseballnowx" and "baseballnowy" variables so that each time the loop runs the baseball will move. Calculating the next x and y coordinates where the baseball should move to isn't as easy as it sounds. Fortunately we have a handy *lerp* code block! "Lerp" is short for [linear interpolation](https://en.wikipedia.org/wiki/Linear_interpolation). When given two numbers, *lerp* returns a number that is between them using a percentage. Since we need to calculate both an x and a y coordinate for the baseball to move to, we are going to use the *lerp* code block twice inside our loop, once for "baseballnowx" and a second time for "baseballnowy".
    1. Drag a new "set variable" code block from the Variables tray and attach it to the bottom of the "Baseball: move to x" code block. Change "item" to "baseballnowx".
    1. Drag a new "lerp from 0 to 200 % 50" code block from the Math tray and attach it to the right of the "set baseballnowx to" codeblock you just created.  
        ![00-040-050](../images/00-040-050.math.lerp.jpg)  
        **figure 00-040-050** "Lerp" code block from the Math tray
        1. Change 0 to the variable "alienx". This means the x coordinate range will always start at the same x position as the alien.
        1. Change 200 to the variable "baseballendx". This means the x coordinate range will end at "baseballendx". We originally set this to 800 so that when the program starts the alien is tossing the baseball from left to right.
        1. Change "50" to the variable "lerppct". This means that each time this code executes, we will use the current value of "lerppct".
            ![07-110](./images/07-110.jpg)  
            **figure 07-110** Move the baseball along the x axis using a *lerp* calculation
    1. Now we need to do the same thing for the y coordinate stored in the "baseballnowy" variable. Let's use a shortcut. Right-click on the "set baseballnowx to" code block and select "Duplicate", attach the new code block to the bottom of the previous code block, and then make the following changes:
        1. Change "baseballnowx" to "baseballnowy".
        1. Change "alienx" to "alieny".
        1. Change "baseballendx" to "baseballendy".  
            ![07-120](./images/07-120.jpg)  
            **figure 07-120** Move the baseball along the y axis using a *lerp* calculation
1. We only have one thing left to do to complete our loop. In order to get our baseball to move we need to increase the value of the "lerppct" variable. This can be done easily with a single codeblock.
    1. Drag a new "increment variable" code block from the Math tray and connect it to the bottom of the previous code block.  
        ![00-040-030.math.incrementvariable.jpg](../images/00-040-030.math.incrementvariable.jpg)  
        **figure 00-040-030** Increment variable code block from the Math tray
    1. Change "item" to "lerppct". This code block will now add 1 to the current value of the "lerppct" variable each time the loop executes and store the result back into the "lerppct" variable.  
    ![07-130](./images/07-130.jpg)  
    **figure 07-130** Increment the value of the "lerppct" variable by one
1. Now comes the really cool part. Let's add a new "Mouse" part to our code, then use [events](https://en.wikipedia.org/wiki/Event-driven_programming) to control where the alien throws the baseball on the canvas.
    1. Add a new *Mouse* part.  
    ![00-500-200](../images/00-500-200.parts.mouse.jpg)  
    **figure 00-500-200** *Mouse* part
    1. Find the *on click* event code block in the *Mouse* tray.  
    ![00-500-280](../images/00-500-280.parts.mouse.onclick.jpg)  
    **figure 00-500-280** *on click* event code block from the *Mouse* tray
    1. Drag a new *on click* event from the *Mouse* tray onto the code space and drop it to the right of the *when app starts* code block. Events are separate pieces of code that run only when the associated event fires, which in this case is when the mouse button is clicked. Click in the canvas a few times, do you see the lightning bolt on the "Mouse: on click" event light up? That means the event is firing, but since there is no code inside the "Mouse: on click" event nothing happens.
    1. Every time the mouse gets clicked we want the alien to start a new baseball toss. To do this we need to reset the values of the "baseballnowx" and "baseballnowy" variables back to where the baseball toss starts, which is where the alien is drawn.
        1. Drag a new "set item to" code block from the Variables tray attach it to the inside of the "Mouse: on click" event. Change "item" to "baseballnowx".
        1. Drag a new "item" code block from the Variables tray and attach it to the end of the "set item to" block you just added. Change "item" to "alienx"
        1. Repeat this same process for the "baseballnowy" variable. Hint: use the "Duplicate" feature as a shortcut.
    1. We are almost done! Now that we've reset the x and y coordinates for the beginning of the baseball toss, we will grab the x and y coordinates from the "Mouse: on click" event and use them to set the x and y coordinates for the end of the baseball toss.
        1. Drag a new "set item to" code block from the Variables tray attach it to the previous code block. Change "item" to "baseballendx".
        1. Drag a new "Mouse: x" code block from the Mouse tray and attach it to the end of the "set item to" block you just added.
        1. Drag a new "set item to" code block from the Variables tray attach it to the previous code block. Change "item" to "baseballendy".
        1. Drag a new "Mouse: y" code block from the Mouse tray and attach it to the end of the "set item to" block you just added. Now click in the canvas, the alien should be tossing the baseball to the location you clicked on.  
        ![07-140](./images/07-140.jpg)  
        **figure 07-140** Use a click event to change the location where the alien tosses the baseball
1. Try changing the position of the alien by moving them from the current position (x=100 and y=400) to a new position further right and up (x=150 and y=350). Remember, we set up variables that are used to set the position where the alien is drawn, so you should only have to change this in one place. Does the code still work after you moved where the alien is drawn?
1. Now share your creation so you can show everybody what an awesome event driven computer animation programmer you are! For a completed version see [baseball-toss-remix-2.kcode](./baseball-toss-remix-2.kcode).
