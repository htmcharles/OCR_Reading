# 📸 OCR Text Reader

A powerful GUI-based Optical Character Recognition (OCR) tool that extracts text from images and live camera feeds using Tesseract OCR engine.

## ✨ Features

- **📁 Image Loading**: Load and process images from your computer (PNG, JPG, JPEG, BMP, TIF, TIFF)
- **📷 Live Camera Feed**: Capture and process text in real-time from your camera
- **🎯 ROI Selection**: Select specific regions of interest by clicking and dragging
- **🔍 Advanced OCR**: Extract text with preprocessing for better accuracy
- **📝 Text Display**: View extracted text in a scrollable text area
- **🖼️ Visual Overlay**: See detected text boxes overlaid on the image
- **⚡ Real-time Processing**: Process camera frames on-the-fly

## 🛠️ Installation

### Prerequisites

- Python 3.7 or higher
- Tesseract OCR engine

### Step 1: Install Tesseract OCR

#### Windows

**Option 1: Using Chocolatey (Recommended)**
```powershell
choco install tesseract -y
```

**Option 2: Manual Installation**
1. Download the installer from [UB Mannheim Tesseract](https://github.com/UB-Mannheim/tesseract/wiki)
2. Run the installer
3. Make sure to check "Add to PATH" during installation
4. Default installation path: `C:\Program Files\Tesseract-OCR`

#### Linux (Ubuntu/Debian)
```bash
sudo apt-get update
sudo apt-get install tesseract-ocr
```

#### macOS
```bash
brew install tesseract
```

### Step 2: Install Python Dependencies

```bash
pip install opencv-python pytesseract pillow numpy
```

Or use the requirements file (if available):
```bash
pip install -r requirements.txt
```

### Step 3: Verify Tesseract Installation

```bash
tesseract --version
```

If Tesseract is not in your PATH, you may need to configure it manually in the code by adding:
```python
import pytesseract
pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
```

## 🚀 Usage

### Running the Application

```bash
python ocr_text_reader.py
```

### How to Use

1. **Load an Image**
   - Click the **"Load Image"** button
   - Select an image file from your computer
   - The image will appear in the canvas area

2. **Start Camera Feed**
   - Click **"Start/Resume Camera"** to activate your webcam
   - The live feed will appear in the canvas
   - Click **"Stop Camera"** to stop the feed

3. **Select Region of Interest (ROI)**
   - Click and drag on the image/camera feed to draw a yellow rectangle
   - This defines the area where OCR will be performed
   - If no ROI is selected, the entire image will be processed
   - Click **"Clear ROI"** to remove the selection

4. **Run OCR**
   - Click **"Run OCR"** to extract text from the image or selected ROI
   - Detected text will be highlighted with green boxes on the image
   - Extracted text appears in the text area at the bottom
   - Status messages appear in the blue status bar

5. **View Results**
   - Extracted text is displayed in the scrollable text area
   - Green boxes show detected text regions on the image
   - Red text labels show the detected words

## 🎮 Controls

| Button | Function |
|--------|----------|
| **Load Image** | Open an image file from your computer |
| **Start/Resume Camera** | Start the camera feed or resume after OCR |
| **Stop Camera** | Stop the camera feed |
| **Run OCR** | Extract text from the current image/ROI |
| **Clear ROI** | Remove the selected region of interest |

## 🔧 Technical Details

### Image Preprocessing

The application uses advanced preprocessing techniques to improve OCR accuracy:

1. **Grayscale Conversion**: Converts color images to grayscale
2. **Bilateral Filtering**: Reduces noise while preserving edges
3. **Adaptive Thresholding**: Handles uneven lighting conditions
4. **Binary Conversion**: Creates high-contrast images for better text detection

### OCR Configuration

- **PSM Mode**: Page Segmentation Mode 6 (assumes uniform block of text)
- **Confidence Threshold**: Only displays text with confidence > 10%
- **Engine**: Tesseract OCR 4.x or 5.x

### Camera Settings

- **Default Camera**: Camera index 1 (change to 0 for built-in webcam)
- **Frame Rate**: ~30 FPS
- **Resolution**: Depends on camera capabilities

## 📋 Requirements

```
opencv-python>=4.5.0
pytesseract>=0.3.0
Pillow>=8.0.0
numpy>=1.19.0
```

## 🐛 Troubleshooting

### Tesseract Not Found Error

**Error**: `TesseractNotFoundError: tesseract is not installed or it's not in your PATH`

**Solution**:
1. Verify Tesseract is installed: `tesseract --version`
2. Add Tesseract to your system PATH
3. Or manually configure the path in the code (see Installation Step 3)

### Camera Not Opening

**Error**: `Camera Error: Cannot open camera`

**Solution**:
1. Check if another application is using the camera
2. Try changing camera index from `1` to `0` in line 173:
   ```python
   self.video_capture = cv2.VideoCapture(0)  # Change 1 to 0
   ```
3. Verify camera permissions in your OS settings

### Poor OCR Accuracy

**Solutions**:
- Ensure good lighting conditions
- Use higher resolution images
- Select a smaller ROI around the text
- Make sure text is clear and not blurry
- Try different angles or distances for camera feed

### Import Errors

**Error**: `ModuleNotFoundError: No module named 'cv2'`

**Solution**:
```bash
pip install opencv-python pytesseract pillow numpy
```

## 💡 Tips for Best Results

1. **Lighting**: Ensure even, bright lighting on the text
2. **Contrast**: High contrast between text and background works best
3. **Resolution**: Higher resolution images produce better results
4. **Angle**: Keep text as straight as possible (not tilted)
5. **ROI**: Select tight regions around text for better accuracy
6. **Font**: Clear, standard fonts work better than decorative ones
7. **Size**: Larger text is easier to recognize

## 📝 License

This project is open source and available for educational and personal use.

## 🤝 Contributing

Feel free to fork this project and submit pull requests for improvements!

## 📧 Support

If you encounter any issues or have questions, please open an issue on the project repository.

---

**Made with ❤️ using Python, OpenCV, and Tesseract OCR**
# OCR_Reading
