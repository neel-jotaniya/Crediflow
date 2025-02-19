# Crediflow Assignment 

# How to Run the Script

## Prerequisites
Before running the script, ensure you have the following installed:

### 1. Install Required Python Libraries
Run the following command to install all necessary dependencies:
```python
pip install openai pytesseract pdf2image pillow
```



### 2. Install Tesseract OCR (Required for Text Extraction)
Tesseract OCR must be installed separately on your system. Follow the instructions based on your OS:

#### For Windows
1. Download the Tesseract installer from:
   https://github.com/UB-Mannheim/tesseract/wiki  
2. Install it and note the installation path (e.g., `C:\\Program Files\\Tesseract-OCR`).
3. Add Tesseract to your system’s PATH:
   - Open **Environment Variables**
   - Edit the **System Path** variable
   - Add: `C:\\Program Files\\Tesseract-OCR`
4. Verify installation by running:

```python
tesseract --version
```
#### For macOS
Install Tesseract via Homebrew:

```python
brew install tesseract
```
#### For Linux
Install via apt (Debian/Ubuntu):

```python
sudo apt update sudo apt install tesseract-ocr
```
### 3. Set Up Tesseract Path in Python (If Needed)
If Tesseract is installed but not detected, manually specify its path in the script before using `pytesseract`:

```python
import pytesseract

# Manually set Tesseract path (only for Windows)
pytesseract.pytesseract.tesseract_cmd = r"C:\\Program Files\\Tesseract-OCR\\tesseract.exe"
```

Steps to Run the Script
Ensure the necessary files are in place

Place the financial report PDF (e.g., vodafone_annual_report_reduced.pdf) in the same directory as the script.
Ensure the vocabulary file (e.g., vocabulary of allowed terms.rtf) is available.
Run the script

Open a terminal or Jupyter Notebook and execute the script step by step.
If running in Jupyter Notebook, execute each cell sequentially.
Check the Outputs

Extracted images will be stored in the images/ folder.
The OCR-extracted text and formatted financial tables will be saved as extracted_tables.txt.
The script will display status messages after each step is completed.




## If I had a few extra days, given optimizations or enhancements would I propose to this task

1. I used OCR (Optical Character Recognition) to extract text from the scanned PDF. Technically, I could use a multimodal model for this, but open-source OCR tools are already really good at handling text extraction from scanned documents. That said, if the document's formatting is all over the place, switching to a multimodal approach might work better.

2. Right now, I’m passing the entire financial report into the model, but that’s not the most efficient way to do it. If financial reports from different companies follow a similar structure, I could optimize the process by only sending the relevant sections to the LLM. This would cut down on token usage and make the process faster. Plus, fine-tuning the LLM specifically for financial reports could be a great long-term solution.

3. Token usage could be reduced even further if we know that the Balance Sheet, Income Statement, and Cash Flow sections always appear on certain pages. Instead of processing the whole document, I could just extract those specific pages and send only what’s necessary to the model. That would make everything way more efficient.