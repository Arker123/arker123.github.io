---
title: Lempel-Ziv-Welch (LZW)
subtitle: Encoder and Decoder
contributors: Arnav Kharbanda 
date: 2022-01-01
image: ../images/LZW.jpg
carousels: 
  - images: 
    - image: ../images/LZW.jpg
      desc: LZW Encoder and Decoder
order: -30
---

Report: [Report](https://docs.google.com/document/d/11D24fY24-y0NNktx6OeTyDhqK6DYTLbzvsZBSECpyhU/edit?tab=t.0#heading=h.mbjsiz6n6jlo)

Github: [Github](https://github.com/Arker123/LZW-encoder-decoder)

### LZW Encoder and Decoder

In this project, I implemented the **LZW (Lempel-Ziv-Welch)** compression algorithm for encoding and decoding grayscale images. Here’s a breakdown of the methodology:

#### LZW Encoder:
- The **LZW encoder** was implemented in Python and takes the **image filename**, **block size**, and **code size** (in bits) as input.
- The image is processed **block by block**, where each block is a square of size **block_size x block_size**. The maximum block size considered is 128, and the value **-1** indicates that the entire image should be processed as one block.
- The encoder builds a **dictionary** based on the input data and replaces frequently occurring sequences of characters with corresponding codes.
- The **code_size** parameter defines the maximum size of the dictionary (in bits). If the dictionary size exceeds the code size, an error message is shown.
- The encoder outputs the LZW-coded file in a **text file format**, where:
  - The first row contains the **height**, **width**, and **block size** of the image.
  - The subsequent rows contain the LZW-coded data for each block, with each code separated by a space.

#### LZW Decoder:
- The **LZW decoder** was also implemented in Python and takes the **LZW-coded filename** as input.
- It first reads the height, width, and block size from the first row of the coded file.
- The decoder processes each block and reconstructs the original grayscale image by **decoding** the LZW-coded data using the same dictionary that was used by the encoder.

### Conclusion:

#### Comparison with Other Compression Algorithms:
- **LZW compression** is an efficient algorithm for **lossless compression** of grayscale images. While other algorithms like **JPEG** or **PNG** might offer higher compression ratios for specific types of data, **LZW** remains a versatile and reliable algorithm suitable for a variety of applications.

#### Limitations:
- **LZW compression** may not perform well for highly **complex images** or **data with high levels of noise**, as these can lead to **lower compression ratios** and **longer encoded data**. In such cases, other compression algorithms may be more effective.