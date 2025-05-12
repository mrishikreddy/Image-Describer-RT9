# Image Describer

Welcome to the **Image Describer** project, a Python-based application that generates descriptive captions for images using the BLIP (Bootstrapping Language-Image Pre-training) model from Salesforce. This project leverages a Gradio interface to provide an interactive web-based tool for uploading images and receiving captions, making it accessible and user-friendly for exploring vision-language models.

## Table of Contents
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [How It Works](#how-it-works)
- [Model](#model)

## Features
- **Image Captioning**: Generates natural language descriptions for uploaded images using the BLIP model.
- **Interactive Interface**: Provides a web-based Gradio interface for easy image uploads and caption display.
- **Pre-trained Model**: Utilizes Salesforce's BLIP model for high-quality caption generation.
- **Error Handling**: Includes basic error handling to manage invalid inputs or processing issues.
- Built with Python libraries: Gradio, Transformers, and PIL for seamless image processing and model integration.

## Installation
To set up the **Image Describer** project, follow these steps:

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-username/image-captioning-blip.git
   cd image-captioning-blip
   ```

2. **Install Dependencies**:
   Ensure you have Python 3.8+ installed. Install the required libraries using pip:
   ```bash
   pip install gradio transformers torch pillow
   ```
   Note: The `torch` library is required by the Transformers library for model inference. Install `torch` compatible with your system (CPU or GPU) as per [PyTorch's installation guide](https://pytorch.org/get-started/locally/).

3. **Run the Script**:
   Execute the Python script to launch the Gradio interface:
   ```bash
   python image_captioning.py
   ```

   This will start a local web server and provide a URL (e.g., `http://127.0.0.1:7860`) to access the interface in your browser.

## Usage
Running the script launches a Gradio web interface with the following steps:
1. Open the provided URL in your browser.
2. Upload an image using the interface's image upload component (accepts common formats like PNG, JPEG).
3. View the generated caption displayed as text output.

Example:
- Upload an image of a dog playing in a park.
- Output: "A dog is playing with a ball in a grassy park."

To modify the script (e.g., use a different BLIP model variant or customize the interface), edit the model initialization or Gradio interface parameters in the code.

## How It Works
The project uses the BLIP model to generate captions for images. Here's a breakdown:

### Model Initialization
- **Processor**: Loads the `BlipProcessor` from `Salesforce/blip-image-captioning-base` to preprocess images and tokenize outputs.
- **Model**: Loads the `BlipForConditionalGeneration` model for generating captions based on image inputs.

### Image Processing
- **Input**: Accepts a PIL Image object via the Gradio interface.
- **Preprocessing**: The processor converts the image into a tensor format suitable for the model.

### Caption Generation
- **Inference**: The model generates a sequence of token IDs based on the processed image.
- **Decoding**: The processor decodes the token IDs into a human-readable caption, skipping special tokens.

### Gradio Interface
- **Setup**: Creates a web interface with an image input and text output using Gradio.
- **Function**: The `caption_image` function handles image input, calls the `generate_caption` function, and returns the caption or an error message.

## Model
The project uses the **BLIP (Bootstrapping Language-Image Pre-training)** model (`Salesforce/blip-image-captioning-base`), a vision-language model pre-trained on large-scale image-text pairs. It excels at generating descriptive captions for a wide range of images.

Source: [Hugging Face Model Hub](https://huggingface.co/Salesforce/blip-image-captioning-base).
