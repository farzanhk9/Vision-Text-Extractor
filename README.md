# A modern AI tool to extract text from images using Google's Tesseract OCR.
import pytesseract
from PIL import Image
import os

def extract_text_from_image(image_path):
    try:
        # Load the image and perform OCR
        img = Image.open(image_path)
        text = pytesseract.image_to_string(img)
        
        return {
            "status": "Success",
            "file": os.path.basename(image_path),
            "extracted_text": text.strip()
        }
    except Exception as e:
        return {"status": "Error", "message": str(e)}

# Note: Requires Tesseract-OCR installed on your system
if __name__ == "__main__":
    path = "sample_image.png" # Replace with your image file
    result = extract_text_from_image(path)
    print(result)
