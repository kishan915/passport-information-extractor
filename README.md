# Passport Information Extractor

A Python-based project that uses **OpenCV** and **Tesseract OCR** to extract text from passport images and parse the **Machine Readable Zone (MRZ)** to obtain important passport information.

## Features

* Extracts text from passport images using **Tesseract OCR**
* Processes passport images using **OpenCV**
* Detects and extracts the last two MRZ lines
* Parses MRZ data into structured information
* Extracts:

  * Document Type
  * Country Code
  * Surname
  * Given Names
  * Passport Number
  * Nationality
  * Date of Birth
  * Gender
  * Date of Expiry

## Technologies Used

* **Python**
* **OpenCV (`cv2`)**
* **Tesseract OCR**
* **Pytesseract**

## Project Structure

```text
passport-information-extractor/
│
├── passport_mrz.py
├── pass image.jpg
└── README.md
```

## How It Works

The project follows these basic steps:

1. **Load Passport Image**

   * OpenCV reads the passport image.

2. **Image Preprocessing**

   * The image is converted from BGR to grayscale to improve OCR processing.

3. **OCR Text Extraction**

   * Tesseract OCR detects and extracts the text from the image.

4. **MRZ Detection**

   * The extracted text is split into individual lines.
   * The last two lines are considered the MRZ lines.

5. **MRZ Parsing**

   * The MRZ information is divided into specific fields such as passport number, nationality, date of birth, gender, and expiry date.

6. **Display Information**

   * The extracted information is displayed in a structured format in the terminal.

## Installation

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/passport-information-extractor.git
cd passport-information-extractor
```

### 2. Install Required Python Libraries

```bash
pip install opencv-python pytesseract
```

### 3. Install Tesseract OCR

Tesseract OCR must be installed separately on your system.

After installation, make sure Tesseract is available in your system PATH.

For Windows, if required, you can specify the Tesseract executable path in Python:

```python
pytesseract.pytesseract.tesseract_cmd = r'C:\Program Files\Tesseract-OCR\tesseract.exe'
```

## How to Run

Place your passport image in the project directory and update the image path in the Python file:

```python
image_path = "pass image.jpg"
```

Then run:

```bash
python passport_mrz.py
```

## Example Output

```text
Extracted Text:
P<INDDOE<<JOHN<<<<<<<<<<<<<<<<<<<<
A12345678<IND9001011M3001012<<<<<<<<

Parsed MRZ Information:
{
    "Document Type": "P",
    "Country Code": "IND",
    "Surname": "DOE",
    "Names": "JOHN",
    "Passport Number": "A12345678",
    "Nationality": "IND",
    "Date of Birth": "900101",
    "Gender": "M",
    "Date of Expiry": "300101"
}
```

> **Note:** The example above uses dummy passport information for demonstration purposes.

## MRZ Information

The project is designed around the standard passport MRZ format.

For example:

```text
P<INDDOE<<JOHN<<<<<<<<<<<<<<<<<<<<
A12345678<IND9001011M3001012<<<<<<<<
```

The parser identifies different sections of these lines and converts them into readable fields.

## Limitations

* OCR accuracy depends on the quality and orientation of the passport image.
* The current implementation assumes that the **last two extracted lines are the MRZ lines**.
* The project currently focuses on a standard two-line passport MRZ format.
* Additional image preprocessing could improve OCR accuracy.
* MRZ checksum validation is not currently implemented.

## Future Improvements

* Add advanced image preprocessing and noise removal
* Automatically detect the MRZ region
* Implement MRZ checksum validation
* Add support for different document types and MRZ formats
* Create a graphical user interface (GUI)
* Export extracted information to JSON/CSV
* Improve OCR accuracy using image resizing and thresholding
* Add error handling for invalid or incomplete MRZ data

## Privacy & Security

This project is intended for **educational and development purposes**.

Do not upload or commit real passport images or sensitive personal information to a public GitHub repository. Use **dummy or sample passport data** when demonstrating the project.

## License

This project is available for educational and personal development purposes. You may modify and improve the code according to your requirements.

---

### Project

**Passport Information Extractor**

Built with **Python, OpenCV, and Tesseract OCR** to demonstrate passport text extraction and MRZ parsing.
