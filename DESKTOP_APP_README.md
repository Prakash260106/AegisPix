# Image Decryption Viewer - Desktop Application

A standalone desktop application that allows you to open and decrypt `.pwimg` files directly in your system's default image viewer without needing a website.

## Features

✅ **Direct File Opening** - Double-click `.pwimg` files to decrypt and view  
✅ **Password Protected** - Enter password to decrypt images  
✅ **Default Viewer** - Opens images in Windows Photo Viewer or your default image app  
✅ **Offline** - Everything happens locally on your computer  
✅ **Auto Cleanup** - Temporary files are automatically deleted after viewing  
✅ **Multiple Formats** - Supports JPG, PNG, GIF, WebP, BMP  

## Installation

### Option 1: Run as Python Script (Requires Python)

1. **Install Python 3.8+** from [python.org](https://www.python.org/downloads/)

2. **Install dependencies:**
   ```cmd
   pip install cryptography
   ```

3. **Run the application:**
   ```cmd
   python decrypt_viewer.py
   ```

### Option 2: Create Standalone .EXE (Recommended)

1. **Install PyInstaller:**
   ```cmd
   pip install pyinstaller cryptography
   ```

2. **Build the executable:**
   ```cmd
   pyinstaller decrypt_viewer.spec
   ```

3. **Find your executable:**
   - The `.exe` file will be in the `dist/` folder
   - You can move it anywhere and run it directly

### Option 3: File Association (Windows)

To open `.pwimg` files by double-clicking them:

1. **Build the executable** (Option 2 above)

2. **Right-click a `.pwimg` file** → "Open with" → "Choose another app"

3. **Select the `ImageDecryptionViewer.exe`** and check "Always use this app"

4. **Now you can double-click any `.pwimg` file** to decrypt and view!

## Usage

### Basic Usage:
```cmd
ImageDecryptionViewer.exe
```
A dialog will appear asking you to select a `.pwimg` file.

### Direct File Opening:
```cmd
ImageDecryptionViewer.exe "path\to\file.pwimg"
```
Or simply **double-click** the `.pwimg` file if file association is set up.

### Workflow:
1. Double-click (or open) a `.pwimg` file
2. Enter the password when prompted
3. The decrypted image opens in your default image viewer
4. The temporary file is automatically deleted when you close the image

## How It Works

1. **Decrypts** the `.pwimg` file using the password you provide
2. **Detects** the image format (JPG, PNG, etc.) automatically
3. **Creates** a temporary image file
4. **Opens** it with Windows default image viewer using `os.startfile()`
5. **Cleans up** the temporary file automatically

## Security

- ✅ Uses **AES-256-GCM encryption** (military-grade)
- ✅ **PBKDF2** key derivation with 100,000 iterations
- ✅ All processing happens **offline** on your computer
- ✅ No data is uploaded or transmitted anywhere
- ✅ Temporary files are deleted after viewing

## System Requirements

- **Windows 7+** (or Windows 10/11 recommended)
- **Python 3.8+** (if running as script)
- **50 MB disk space** (for standalone executable)

## Technical Details

### File Format (.pwimg)
```
Magic: 'PWIMG' (5 bytes)
Version: 1 (1 byte)
Salt: 16 bytes (random)
IV: 12 bytes (random)
Encrypted Data: Image bytes (AES-256-GCM)
```

### Encryption Details
- **Algorithm:** AES-256-GCM
- **Key Derivation:** PBKDF2-SHA256 with 100,000 iterations
- **IV Size:** 12 bytes (96 bits)
- **Authentication:** GCM provides authentication

## Troubleshooting

### "Invalid file format" error
- The file might be corrupted or not a `.pwimg` file
- Make sure you selected the correct file

### "Decryption failed" error
- Wrong password was entered
- The file is corrupted
- Password contains special characters that weren't typed correctly

### File doesn't open in image viewer
- Your default image viewer might not be properly set
- Try right-clicking the decrypted image and selecting "Open with" → preferred viewer

### Can't find the .exe after building
- Check the `dist/` folder in your project directory
- The executable will be named `ImageDecryptionViewer.exe`

## Encryption Tool

To encrypt images and create `.pwimg` files, use the web-based encryption tool:
- Visit `encrypt-image.html` in a browser
- Or build a Python encryption tool using the same format

## License

Free to use and modify.

## Support

For issues or questions, check the code comments or rebuild the application.
