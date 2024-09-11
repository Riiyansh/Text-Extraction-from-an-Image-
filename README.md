# Text Extraction from Images using Tesseract and OpenCV

## Overview
This project focuses on extracting text from images using Tesseract OCR and applying basic image processing techniques with OpenCV to enhance text extraction accuracy. This can save time and effort compared to manual typing.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [Image Preprocessing Steps](#image-preprocessing-steps)
- [Text Extraction](#text-extraction)
- [Advanced Image Processing](#advanced-image-processing)
- [Conclusion](#conclusion)
- [Scope](#scope)

## Installation
To set up the environment, follow these steps:

1. **Install Tesseract and Required Libraries**:
   ```bash
   !apt install tesseract-ocr libtesseract-dev libmagickwand-dev
Install Python Libraries:

Copy
!pip install pytesseract wand opencv-python
Download Tesseract Trained Data:

Copy
import requests

r = requests.get("https://raw.githubusercontent.com/tesseract-ocr/tessdata/4.00/ind.traineddata", stream=True)
with open("/usr/share/tesseract-ocr/4.00/tessdata/ind.traineddata", "wb") as file:
    for block in r.iter_content(chunk_size=1024):
        if block:
            file.write(block)
## Usage
Import Required Libraries:

Copy
from PIL import Image
import pytesseract
import cv2
import numpy as np
from pytesseract import Output
import re
Read and Resize Image:

Copy
image = Image.open(requests.get('https://i.stack.imgur.com/pbIdS.png', stream=True).raw)
image = image.resize((300, 150))
image.save('sample.png')
Image Preprocessing Steps
Grayscale Conversion: Convert images to grayscale for simpler processing.
Noise Removal: Apply median blurring to reduce noise.
Thresholding: Use binary thresholding to distinguish text from the background.
Erosion: Erode the image to remove small noise points.
Morphological Transformations: Open small holes inside foreground objects.
Text Extraction
Use Tesseract to extract text from the preprocessed image:

Copy
custom_config = r'-l eng --oem 3 --psm 6'
text = pytesseract.image_to_string(image, config=custom_config)
Clean the extracted text by removing unwanted symbols.

## Advanced Image Processing
Canny Edge Detection: Detect edges in the image.
Deskewing: Correct skew in images for better alignment.
Template Matching: Match templates within images to find specific patterns.
## Conclusion
This project demonstrates the use of Tesseract and OpenCV for Optical Character Recognition (OCR). By preprocessing images and applying transformations, the accuracy of text extraction can be significantly improved.

## Scope
This technology can be beneficial for organizations needing to automate data entry from printed documents, process invoices, or digitize handwritten notes, among other applications.
