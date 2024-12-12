---
home: 10
title: Image Morphing
subtitle: Delauney Triangulation | dlib
contributors: Arnav Kharbanda
date: 2022-01-01
image: ../images/morphing.jpg
carousels: 
  - images: 
    - image: ../images/morphing.gif
      
order: -30
---
### Image Morphing

This project was focused on creating smooth image transitions using **dlib** and **Delaunay triangulation**. Here's how it works:

1. **Tie Point Generation**:  
   I used **dlib** to generate corresponding tie points between two images. These points were saved into a `.node` file, which includes key coordinates that define the features for morphing the images.

2. **Triangle Generation**:  
   The **'triangle' executable** processes the `.node` file to create triangles based on the tie points. These triangles are used for the morphing process.

3. **Delaunay Triangulation**:  
   **Delaunay's triangulation algorithm** divides the image into triangles, helping to smoothly interpolate between the two images during morphing.

4. **Image Interpolation**:  
   I generated 101 images by gradually varying the alpha parameter from 0 to 1 (in steps of 0.01). Each image represents a different blend between the two source images.

5. **GIF Creation**:  
   The generated images were converted into a **GIF** using the **PIL (Python Imaging Library)**, with the final result saved as `output.gif` to show the smooth transition.

### Conclusion:
This project was a fun and interesting one to work on. It allowed me to experiment with image processing techniques like Delaunay triangulation and tie point generation, and it was exciting to see the morphing process come to life in the final GIF!