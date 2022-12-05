 - following are the different ways to enhance the image for ocr extraction.
#### changing contrast1
	 1. converting to LAB space
			1.  L – Lightness ( Intensity ).
			2.  a – color component ranging from Green to Magenta.
			3.  b – color component ranging from Blue to Yellow.
	2. applying CLAHE to l channel, which is a variant of adaptive histogram equalisation.
	3. adding the a,b channel to l channel and givving the output
 
```
def contrast(img):
    # converting to LAB color space
    lab= cv2.cvtColor(img, cv2.COLOR_BGR2LAB)
    l_channel, a, b = cv2.split(lab)

    # Applying CLAHE to L-channel
    # feel free to try different values for the limit and grid size:
    clahe = cv2.createCLAHE(clipLimit=2.0, tileGridSize=(8,8))
    cl = clahe.apply(l_channel)

    # merge the CLAHE enhanced L-channel with the a and b channel
    limg = cv2.merge((cl,a,b))

    # Converting image from LAB Color model to BGR color spcae
    enhanced_img = cv2.cvtColor(limg, cv2.COLOR_LAB2BGR)
    return enhanced_img
```
#### changing contrast2 along with brightness
		1. basically adding two images (in this case its the same image twice) with different weights (alpha,gamma) which are calculated usin gthe formula mentioned below
```
def apply_brightness_contrast(input_img, brightness = 0, contrast = 0):
    
    if brightness != 0:
        if brightness > 0:
            shadow = brightness
            highlight = 255
        else:
            shadow = 0
            highlight = 255 + brightness
        alpha_b = (highlight - shadow)/255
        gamma_b = shadow
        
        buf = cv2.addWeighted(input_img, alpha_b, input_img, 0, gamma_b)
    else:
        buf = input_img.copy()
    
    if contrast != 0:
        f = 131*(contrast + 127)/(127*(131-contrast))
        alpha_c = f
        gamma_c = 127*(1-f)
        
        buf = cv2.addWeighted(buf, alpha_c, buf, 0, gamma_c)

    return buf

```
#### Gamma correction (Power Law Transform)
	1. image pixel -> scaled to 0-1 -> apply the formula mentioned in code -> rescaled to 0-255
	2. gamma<1  -> will shift image to darker side
	3. gamma>1  -> will shift the image appear lighter
	4. table in the code is the dictionary having input pixel to output gamma corrected values
	5. LUT applies the taransformation in the table to the pixel values of the image.

```
def gammaCorrection(src, gamma):
    invGamma = 1 / gamma

    table = [((i / 255) ** invGamma) * 255 for i in range(256)]
    table = np.array(table, np.uint8)

    return cv2.LUT(src, table)
```