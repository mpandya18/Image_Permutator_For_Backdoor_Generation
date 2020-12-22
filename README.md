# Image_Permutator_For_Backdoor_Generation

This tool has been designed to generate precise pixel-level mutations in images for the purposes of rigorous analysis of backdoor attacks in deep neural networks.

Upon running, the tool will ask for user input in the format “X x Y” where X and Y are real, positive integers representing the pixel width and pixel height. This is to specify the pixel resolution for a template that will carry out the pixel mutations. For example:

25 x 25  - specifies an image template of twenty-five by twenty-five pixel resolution. 1 x 1 is the first top left corner pixel and 25 x 25 is the final bottom right corner pixel.

In the next step the user specifies whether a "low_level" or "template" perturbation is desired.

## Template perturbation

In this mode the user inputs the shape, colour, dimensions or radius and starting locus for the template perturbation. Currently square, rectangle, circle regular as well as non-regular polygons are supported shapes along with the colours of the rainbow. The option to specify custom colours via RGB values is also there.

Square Example: square yellow 10 x 10 5 x 5 - Here 10 x 10 is the dimension of the square perturbation while 5 x 5 is the pixel point on the image that the top left of the square will be at.

Circle Example: circle indigo 10 7 x 8 - Here 10 is the radius of the circle (in pixels) while 7 x 8 is the pixel point at which the centre of the circle lies.

Regular Polygon Example: regular_polygon 125_253_86 8 100 500 x 500 - Here 125, 253 and 86 are RGB values respectively, 8 is the number of sides the regular polygon should have, 100 is the radius of the polygon and 500 x 500 is the centre locus of the polygon in pixels.

Non-Regular Polygon Example: polygon violet 360 124 345 645 324 234 432 134 - Here all numbers are x and y coordinates of all the vertices of the polygon respectively i.e. (360, 124), (345, 645) etc.

## Low level perturbation

There are two submodes to low level perturbation: absolute and relative.

User input requires that each individual pixel to be mutated has to be specified by inputting the pixel of the form “X x Y” where X and Y represent the specific pixel at point (X,Y) on the image template that is graphically represented. On the same line the mutation for RGB in values has to be specified. This has to be done for every pixel that needs mutating. This is followed by either a 1 for absolute pixel value or 0 or relative pixel value mutation. For example:

14 x 17 10 -19 130 0 - specifies that the pixel at point 14 x 17 undergoes mutation of +10 R value, -19 G value and +130 B value.

13 x 19 25 113 12 1 - specifies that the pixel at point 13 x 19 is absolutely mutated to the new values of 25 R, 113 G and 12 C.

Note that pixel mutations that result in RGB values lower than 0 or greater than 255 only permute to 0 or 255 respectively. When no more mutations are desired, inputting “end” into user input puts an end to the process and the tool then proceeds to carry out the permutation.
