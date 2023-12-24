# Template-Matching-
Template Matching:
import cv2
import numpy as np

def template_matching(image_path, template_path):
    image = cv2.imread(image_path)
    template = cv2.imread(template_path)
    result = cv2.matchTemplate(image, template, cv2.TM_CCOEFF_NORMED)
    min_val, max_val, min_loc, max_loc = cv2.minMaxLoc(result)

    top_left = max_loc
    bottom_right = (top_left[0] + template.shape[1], top_left[1] + template.shape[0])

    cv2.rectangle(image, top_left, bottom_right, (0, 255, 0), 2)

    cv2.imshow('Template Matching', image)
    cv2.waitKey(0)
    cv2.destroyAllWindows()

# Example usage
image_path = 'path/to/your/image.jpg'
template_path = 'path/to/your/template.jpg'
template_matching(image_path, template_path)
