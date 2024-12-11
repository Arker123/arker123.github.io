---
title: JPEG Encoder and Decoder
subtitle: Encoder-Decoder Implementation and Parameter Analysis
contributors: Arnav Kharbanda 
date: 2022-01-01
image: ../images/panorama.png
order: -30
---
Github: [github](https://github.com/Arker123/JPEG-encoder-decoder)
Report: [Report](https://docs.google.com/document/d/13S5LMSplLXagIZxnNmZ9qI0E7nyHwTCgcz1mlRtyH5Y/edit?tab=t.0#heading=h.mbjsiz6n6jlo)

### JPEG Encoder and Decoder Implementation

The JPEG encoder and decoder were implemented with the following features:

- **RGB to YUV Conversion**: The input image is first converted from RGB to YUV format, with grayscale images treated separately.
- **JPEG Encoder**:
  - The image is divided into 8x8 blocks (default), and each block undergoes **Discrete Cosine Transform (DCT)** to convert pixel values from the spatial domain to the frequency domain.
  - The DCT coefficients are then quantized using a predefined **quantization matrix** to control compression and lossiness.
  - A **zig-zag scan** is applied to the quantized coefficients, converting them to a 1D array.
  - Zero coefficients at the end of the array are omitted for further compression, with the number of coefficients to retain controlled via the `num_coeff` parameter.
- **JPEG Decoder**:
  - The compressed image is decompressed to retrieve the quantized DCT coefficients.
  - These coefficients are multiplied by the inverse quantization matrix, followed by the **inverse DCT** to reconstruct the image in the spatial domain.
  - The image, now in YUV format, is converted back to **RGB** format for display or storage.

### Parameters Variation:
- **Number of Coefficients**: Varying the number of coefficients sent influences both the **compression ratio** and **image quality**.
- **Block Size**: The block size (e.g., 8x8, 4x4) directly impacts compression efficiency and image quality.
- **Normalization/Quantization Matrix**: The quantization matrix size (e.g., 16x16, 8x8) affects both the image quality and compression ratio, where larger matrices generally lead to better quality but lower compression.

### Results:
- **Compression Ratio**: The highest compression ratio was observed when using an 8x8 block size, balancing compression efficiency and image quality.
- **Image Quality**: Using fewer coefficients results in higher compression ratios but noticeable quality loss. Increasing the number of coefficients improves image quality but reduces compression.
- **Quantization Impact**: Adjusting the quantization matrix (e.g., using bicubic interpolation) allowed for fine-tuning the balance between **compression ratio** and **image quality**.

### Conclusion:
The JPEG compression algorithm demonstrates significant flexibility through parameter tuning, balancing between compression and image quality. Reducing the number of coefficients and changing block sizes can significantly alter results. The YUV conversion plays a key role in enhancing compression efficiency, resulting in reduced data size. However, JPEG’s lossy nature may not be suitable for all applications, especially those requiring high fidelity or transparency.