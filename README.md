# inpainting
inpainting method based upon the paper "Object Removal by Exemplar-Based Inpainting"

## inpainting Class

There is a class Criminisi_Inpaint which has the constructor which takes
how argument an image, a mask; the size of the patch (standard is 9); the
size of the square structuring element for the erosion operation (standard is 3,
to obtain an outline of size 1); the size of the square structuring element for
the dilation operation (standard is 5); 
Images can be supplied in RGB or in gray scale;

### methods:

•apply_erosion(self): 
Creates a list of pixels that belong to the outline
of the mask, given by the difference between the mask and the eroded mask.

• apply_dilation(self): 
Creates a list of pixels that belong to the outer contour of the mask given by the difference between the mask dilated by
a structuring element of size 5 (to avoid the discontinuity given by the
mask) and the mask dilated by a structuring element of size 3.

• find_nearest_dilation(self, indexes of contour, indexes of dilation):
Find for each point in the outline of the mask, the closest point
in the outer contour, so that the derivative of the image can be taken to
calculates it from Data.

• calculate_confidence(self): 
Calculates the Confidence value for each pixel in the mask outline as explained in the paper.

• calculate_data(self):
Calculates the value of Data for each pixel in the mask outline as explained in the paper.

• find_best_source(self, current_patch, pat_shape): 
Find the best match of an outline patch in D.

• inpaint(self, SHOW_STEPS=False, MAX_ITERATIONS=10000):
The main loop of the algorithm. The maximum number of standard iterations
is 10000 and the user has the option to view the painting process by
real time, how in the figure
