[Visit Live Version](https://aefgp.github.io/compiterator/index.html)

[Visit Wiki](https://github.com/AEFGP/AEFGP.github.io/wiki/Compiterator:-The-Chaos-Game)

Compiterator Version 1.12.1
Open index.HTML in Chromium based browsers, this script seems to have really bad performance on other browsers.

The name 'Compiterator' (for "Complex Iterator") is based on the fact the program uses iterations of complex functions. It is meant to be a geometric live interactive way to generate fractals, it is in some sense a mathematical toy.

## Controls

* `space`: Toggle RENDER/EDIT modes     
--EDIT--   
* `L alt` **`HOLD`** + `L mouse`: Add node 
* `L mouse` **`HOLD`**: Delete node  
* `up arrow`: New layer
* `down arrow`: Delete top layer   
* `right arrow`: Next layer 
* `left arrow`: Previous layer   
--RENDER--   
* `"`|`'`: Increase resolution multiplier
* `:`|`;`: Decrease resolution multiplier
* `Q`: Toggle render (freeze)
* `R`: Clear render (and randomise point)
* `U`: Toggle max iteration checking
* `E`: Cycle iteration mode
* `N`: Cycle node exclusion
* `M`: Cycle layer exclusion
* `H`: Jumble node order
* `K`: Jumble layer order
* `C`: Randomise colour settings
* `V`: Randomise render vectors
* `O`: Randomise iteration options
* `P`: Randomise attractor nodes / points
* `I`: Randomise number of layers and numbers of points
* `shift`: Toggle toggling of N and M to their broken functions in prior versions 
* `~`: Cycle mouse-selector mode
* `W`: Move mouse-selector point up
* `A`: Move mouse-selector point left
* `S`: Move mouse-selector point down
* `D`: Move mouse-selector point right
* `1`: Complex parameter mouse-selector mode
* `2`: Iterated point mouse-selector mode
* `3`: Iterated cluster mouse-selector mode
* `4`: Latest node mouse-selector mode
* `5`: Probability mouse-selector mode
* `6`: Render origin mouse-selector mode
* `7`: Render rotation mouse-selector mode
* `8`: Colour origin mouse-selector mode
* `9`: Colour rotation mouse-selector mode
* `B`: Cycle colour mode
* `<`|`,`: Decrease colour cycle depth
* `>`|`.`: Increase colour cycle depth
* `?`|`/`: Dump parameters into browser console
* `enter`: Save Image

## Instructions
In **edit mode** (default state):        

   Place nodes in different layers to inform the kind of image that will be generated in render mode.   
   Use the up and down arrow keys to increase or decrease the total number of layers.   
   Use the right and left arrow keys to select the current layer that the new node will be part of. 
  
   Alt + Left Click to place a node at the cursor, an already existing node at the cursor will be overridden.   
   Hold left click to remove any nodes at the cursor, it will not remove a node if it is the last of its layer.
   Layers that don't have any nodes are considered to have a node at the center of the screen.

Press spacebar to move to render mode.   

In **render mode**:   
You can save the image in render mode using the `ENTER` key.   
_NOTE: If your window resizes due to the downloads bar popping up it will clear the render mode but the image can still be saved._   

To clear the screen press `R` or go to edit mode and then back to render.   
Pressing `Q` toggles the rendering so that no changes occur, useful for pausing to inspect and for swapping modes for creative combinations.      

Pressing `E` will cycle the different algorithms for the chaos game, it will not clear the screen.   
1. linear interpolation algorithm.
2. constant distance algorithm.    
3. linear interpolation algorithm with exponential sum output parameter
4. linear interpolation algorithm with broken exponential sum output parameter
5. Polynomial function iteration.
6. Polynomial Newton's method iteration. 
7. 5 w/ broken z
8. 6 w/ broken z
9. 5 w/ broken z + broken poly
10. 6 w/ broken z + broken poly
11. 5 w/ broken broken z + broken broken poly + broken PF
12. old exponential & constant distance iteration
13. old exponential iteration

 
Pressing `~` will cycle the different mouse-selector modes.     
The mouse (or `WASD` keys) will set/move the point that controls different parameters:   
1. Complex parameter for the various iteration modes.
1. Location of the iterated point, can be used to demonstrate the attractor properties.
1. Point at which the plot is drawn towards, also useful to demonstrate the attractors.
1. Most recently created node, useful for making small adjustments to the shape.
1. Probabilities, with the probability of iterated point resetting as x and layer swapping as y respectively.
1. Location of the origin of the plot.
1. Rotation & scaling of the plot.
1. Location of the origin for colouring.
1. Rotation & scaling of the colour map.     

You can budge the point specified by the input settings that would otherwise be set by the mouse a small distance from its current position by pressing `WASD` in the way you would expect, `W` = up, `A` = left, `S` = down, `D` = right.    
This can be used to observe how small changes in the current state effect the outcome without having to locate the old point with the mouse.
                           
Pressing `N` and `M` cycle the exclusion algorithm for the nodes and layers, this does not clear the screen. Both default to 0.   
At the value of 1, no longer can the previously chosen item be chosen again.    
Beyond 1 it excludes the "nth" next item from being chosen.     
Use H and K to jumble the node and layer order to explore all the permutations of the exclusion effects.     
If you wish to use the old broken functionality of the node and layer exclusion modes, press `SHIFT`, then press `N` or `M`, then `SHIFT` again.   
The node exclusion or the layer exclusion respectively will work as they did before the fix. (`SHIFT` toggles the `N` and `M` buttons into toggles of the fix independently for either mode)   

You can cycle through different modes of the colours shown by pressing `B`. This will clear the screen.   
The depth to which the colour algorithm refers to can be increased or decreased by using `>` and `<`.    
This will increase the time it takes the render to fill but it can allow for a clearer exploration of the self-similarities and symmetries in the fractal structures produced.

The position of all the attractor nodes can be randomly set using `P`     
The other settings pertaining to the shape of the fractal can be randomly set using `O`      
Colour settings can be randomly set using `C`      
The location, size and rotation of the render can randomly set using `V`        
To randomise the actual number of layers and points for each layer use `I`
The iteration mode is not randomised by any of these settings.

## Background Information
The chaos game involves choosing points in a probabilistic algorithm and iterating the movement by some other algorithm to the chosen point of a tracked point.   
This often produces mathematical attractors, shapes which are approached regardless of the starting value of the iteration given enough iterations.    

This program completes 500 iterations a frame.   
   At 50% (variable) probability each iteration there is a chance that a new layer is chosen at random, this could include the layer previously selected.
   Each iteration in the chosen layer a single node is chosen at random, it also can include the node that was previously selected.    

What layers and nodes can be selected in relevance to the previously selected layers and nodes can be changed.  
The image is coloured based on previous iterations to highlight the fractal elements of the image such as the self-similarities and symmetries.       

Even though the motivation for this project was to generate the chaos game, it also generates other complex iterated function systems, and uses the geometric meanings from the chaos game. For example the polynomial mode generates a polynomial which has the nodes of the current layer as its zeroes. 

There are four algorithms for the iteration with sensible definitions:
- The iterated point moves on a linear interpolation to the chosen node with a complex parameter.     
The parameter, based on the screen position, is mapped from the whole plane into the unit disk.
- The iterated point moves by a rotation of a constant complex vector towards the chosen node.
The parameter, based on the screen position, is mapped in the reals by an exponential and in the imaginary by a branched logarithm.
- The iterated point moves to the output of a polynomial function that has the current layer as zeroes and multiplied by a complex parameter.    
- The iterated point moves according to applications of Newton's method over the same polynomial function as above.

Sometimes the polynomial can escape the canvas, simply refresh the canvas or enable the randomisation or max iterations (max iterations is enabled by default)