# Image_Permutator_For_Backdoor_Generation

This tool has been designed to generate precise pixel-level mutations in images for the purposes of rigorous analysis of backdoor attacks in deep neural networks.

Upon running the tool the user is asked to specify whether backdoors are to be generated in a randomly generated or existing dataset. Input "randomly generated" or "existing" to proceed further. 

Thereafter the tool will ask whether "uniform" or "rigorously characterised" backdoors are to be generated.

## Uniform

If "randomly generated" was inputted, the tool will ask for user input in the format “X x Y” where X and Y are real, positive integers representing the pixel width and pixel height. This is to specify the pixel resolution for a template that will carry out the pixel mutations. For example:

25 x 25  - specifies an image template of twenty-five by twenty-five pixel resolution. 1 x 1 is the first top left corner pixel and 25 x 25 is the final bottom right corner pixel.

The tool will also ask for the number of images to be generated in the dataset.

If "existing" was inputted initially, a filedialog will now open in which the user has to select the folder containing the dataset.

In the next step the user specifies whether a "low_level", "template" or "pattern" perturbation is desired.

### Template perturbation

In this mode the user inputs the shape, colour, dimensions or radius and starting locus for the template perturbation. Currently square, rectangle, circle regular as well as non-regular polygons are supported shapes along with the colours of the rainbow. The option to specify custom colours via RGB values is also there.

Square Example: square yellow 10 x 10 5 x 5 - Here 10 x 10 is the dimension of the square perturbation while 5 x 5 is the pixel point on the image that the top left of the square will be at.

Circle Example: circle indigo 10 7 x 8 - Here 10 is the radius of the circle (in pixels) while 7 x 8 is the pixel point at which the centre of the circle lies.

Regular Polygon Example: regular_polygon 125_253_86 8 100 500 x 500 - Here 125, 253 and 86 are RGB values respectively, 8 is the number of sides the regular polygon should have, 100 is the radius of the polygon and 500 x 500 is the centre locus of the polygon in pixels.

Non-Regular Polygon Example: polygon violet 360 124 345 645 324 234 432 134 - Here all numbers are x and y coordinates of all the vertices of the polygon respectively i.e. (360, 124), (345, 645) etc.

### Low level perturbation

There are two submodes to low level perturbation: absolute and relative.

User input requires that each individual pixel to be mutated has to be specified by inputting the pixel of the form “X x Y” where X and Y represent the specific pixel at point (X,Y) on the image template that is graphically represented. On the same line the mutation for RGB in values has to be specified. This has to be done for every pixel that needs mutating. This is followed by either a 1 for absolute pixel value or 0 or relative pixel value mutation. For example:

14 x 17 10 -19 130 0 - specifies that the pixel at point 14 x 17 undergoes mutation of +10 R value, -19 G value and +130 B value.

13 x 19 25 113 12 1 - specifies that the pixel at point 13 x 19 is absolutely mutated to the new values of 25 R, 113 G and 12 C.

Note that pixel mutations that result in RGB values lower than 0 or greater than 255 only permute to 0 or 255 respectively. When no more mutations are desired, inputting “end” into user input puts an end to the process and the tool then proceeds to carry out the permutation.

### Pattern perturbation

In this mode a filedialog will open and the user has to select an image file consisting of the pattern to be inserted.

Once selected, the tool will ask for input specifying the starting pixel (top-left) location for the pattern to be inserted. This should be inputted in the format X x Y where X is the width and Y is the hight in pixels. For example:

12 x 15 is the pixel at width 12 and height 15 going right and down from the top left at 0 x 0.

## Rigorously Characterised

The aim of rigorous characterisation is to specify clearly the intent of the backdoor attack upon a model. The D5 Mnemonic defines five levels of intent:

Decieve - the aim is to decieve the user, potentially misclassifying output.
Degrade - the aim is to degrade the performance of the model.
Deny - the aim is to deny the service provided by the model
Disrupt - the aim is to disrupt the service provided by the model.
Destroy - the aim is to destroy the service provided by the model.

Three measures are also defined here:

Disruption - a measure of the variation between original and mutated pixel values (values are between 0 and 100). 
Dispersion - a measure of of overall number of mutations per image (values are between 0 and 100).
Stealth - a measure of how difficult the mutation is to detect (values are between 0 and 100).

In descending order, the 5Ds increase the intensity of the disruption level in the attack. Once the user has entered the desired intent, the tool will ask whether values
for Disruption and Dispersion are to be autoset or manually entered. Inputting "auto" will automatically set the disruption within the boundaries specified as per below:

Decieve - 0-20 disruption
Degrade - 20-40 disruption
Deny - 40-60 disruption
Disrupt - 60-80 disruption
Destroy - 80-100 disruption

The dispersion will be allocated randomly a value between 0 and 100.

Inputting "manual" will allow the user to specify the disruption within the given boundaries defined by the intent selected and also the dispersion value.
Once these are specified the tool then proceeds similarly to the "uniform" selection in terms of generating or loading the dataset. The tool will generated randomly
perturbations in each image within the dataset depending on the disruption and dispersion values specified. A higher dispersion will increase the number of mutations, while a higher disruption will increase the value of mutations i.e. the difference between the original and mutated pixel values. The aim is to simulate a backdoor attack upon training data for a model.
