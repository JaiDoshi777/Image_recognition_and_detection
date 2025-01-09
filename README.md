# Image_recognition_and_detection
This project aims to Recognize and detect the contents of one image into another image or multiple images 

This means, for example, if Photo 1 contains a single cereal food box and Photo 2 has multiple cereal food boxes, the code will recognize the cereal food box in Photo 1 and find the same one in Photo 2, even among numerous other cereal food boxes.

The script begins by importing essential libraries, including cv2 for OpenCV functionalities, matplotlib.pyplot for image display, and numpy for numerical operations. A helper function named display is defined to visualize images using Matplotlib with a specified color map.

The main image (reeses_puffs.png) and the target image (many_cereals.jpg) are read in grayscale mode using OpenCV's imread function and displayed using the display function. The core of this project involves feature detection and description using the SIFT (Scale-Invariant Feature Transform) algorithm, which is known for its robustness in identifying features across images.

The SIFT detector is created using cv2.SIFT_create(), and the detectAndCompute method is used to detect key points and compute descriptors for both images (reeses and cereals). The key points (kp1 and kp2) and descriptors (des1 and des2) are obtained for each image.

For matching the descriptors between the two images, utilized the FLANN (Fast Library for Approximate Nearest Neighbors) based matcher. The FLANN matcher is initialized with parameters FLANN_INDEX_KDTREE for the algorithm type, trees for the number of trees in the index, and checks for the number of checks to perform during the search. The knnMatch method is called to perform K-Nearest Neighbors matching between des1 and des2, resulting in a list of matches.

A mask (matchesMask) is created to filter out "bad" matches. Initially, all entries are set to [0, 0], meaning no matches are selected. In the filtering loop, the ratio test is performed to identify good matches by comparing the distances of the two closest matches. If the distance of the first match is less than 0.7 times the distance of the second match, the match is considered good and is included in the mask.

Finally, the cv2.drawMatchesKnn function is used to draw the matches between the two images, with parameters to specify the match color, single point color, match mask, and drawing flags. The resulting image (flann_matches) is displayed using the display function, showing the matched key points between the two images.
