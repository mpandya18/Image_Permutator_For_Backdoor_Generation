# Image_Permutator_For_Backdoor_Generation

This tool has been designed to generate precise pixel-level mutations in images for the purposes of rigorous analysis of backdoor attacks in deep neural networks.

Upon running, the tool will ask for user input in the format “X x Y” where X and Y are real, positive integers representing the pixel width and pixel height. This is to specify the pixel resolution for a template that will carry out the pixel mutations. For example:

25 x 25  - specifies an image template of twenty-five by twenty-five pixel resolution. 1 x 1 is the first top left corner pixel and 25 x 25 is the final bottom right corner pixel.

Thereafter, user input requires that each individual pixel to be mutated has to be specified by inputting the pixel of the form “X x Y” where X and Y represent the specific pixel at point (X,Y) on the image template that is graphically represented. On the same line the mutation for RGB in values has to be specified. This has to be done for every pixel that needs mutating. For example:

14 x 17 10 -19 130 - specifies that the pixel at point 14 x 17 undergoes mutation of +10 R value, -19 G value and +130 B value.

Note that pixel mutations that result in RGB values lower than 0 or greater than 255 only permute to 0 or 255 respectively. When no more mutations are desired, inputting “end” into user input puts an end to the process and the tool then proceeds to carry out the permutation.
