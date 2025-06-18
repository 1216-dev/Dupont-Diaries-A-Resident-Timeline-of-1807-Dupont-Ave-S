# Dupont-Diaries-A-Resident-Timeline-of-1807-Dupont-Ave-S
This project reconstructs a detailed year-by-year timeline of individuals residing at 1807 Dupont Ave S, Minneapolis, MN 55403 using digitized Minneapolis city directories. 

# 🏛️ Historical Resident Timeline Reconstruction for 1807 Dupont Ave S, Minneapolis (1902–1950)

This project aims to create a detailed **year-by-year timeline** of residents living at **1807 Dupont Ave S, Minneapolis, MN 55403**, using **digitized Minneapolis city directories** and advanced AI tools.

The project demonstrates how AI (OCR + LLM) can power the reconstruction of a property's history — a key vision of platforms like HouseNovel.

📍 **Zillow Reference:**  
[https://www.zillow.com/homedetails/1807-Dupont-Ave-S-Minneapolis-MN-55403/1951320_zpid/](https://www.zillow.com/homedetails/1807-Dupont-Ave-S-Minneapolis-MN-55403/1951320_zpid/)

---

## 📁 Repository Structure

├── final_images_19xx/
│ ├── page_120.jpg # Stitched full-page image
│ ├── page_120_output.jpg # Annotated OCR result with bounding boxes
│ ├── page_120_raw_text.txt # Raw OCR text
│ ├── page_120_structured.json # Gemini-generated structured data
├── src/ # Python scripts (tile downloader, OCR, JSON builder, etc.)
├── timeline_output.txt # Final year-wise resident timeline
├── main_notebook.ipynb # Complete workflow notebook
├── report.tex # Final LaTeX report (Overleaf-compatible)
└── README.md

---

## 🧠 Project Overview

### 🎯 Objective

To compile a structured, year-wise timeline (1902–1950) of residents for the Minneapolis address `1807 Dupont Ave S` by:

- Extracting relevant resident entries from city directories
- Parsing names, occupations, employers, and spouses
- Matching address variations and inconsistencies
- Validating with image and text cross-references

---

## 🔄 Workflow Summary

### 📌 Phase 1: Data Collection & Structuring

1. **Image Tile Download & Assembly**
   - Downloaded 6 tiles per page from the Hennepin County archive.
   - Stitched into a single full-page image using OpenCV.

2. **OCR Text Extraction**
   - Applied `EasyOCR` to extract text and bounding boxes.
   - Saved output images with bounding boxes annotated.
   - Stored raw text for each page.

3. **Text Correction (Gemini)**
   - Cleaned raw OCR output using Gemini 1.5.
   - Removed common OCR errors, restored formatting and names.

4. **Structured Data Extraction (Gemini)**
   - Prompted Gemini to extract the following fields into structured JSON:
     - `First_Name`, `Last_Name`
     - `Spouse_Name`
     - `Occupation`
     - `Employer_Business_Name_Address`
     - `Home_Address`

5. **File Organization**
   - Each year has its own folder with:
     - Page image
     - Annotated OCR output
     - Raw text file
     - Structured JSON

🔗 All output files are available here:  
**Google Drive Folder:**  
[https://drive.google.com/drive/folders/17-nVEvwAndcJTtCpNaTi08oHCIQamqdZ](https://drive.google.com/drive/folders/17-nVEvwAndcJTtCpNaTi08oHCIQamqdZ)

---

### 📌 Phase 2: Timeline Construction – 1807 Dupont Ave S

1. **Address Normalization**
   - Used regex to match address variants:
     - "1807 Dupont Ave S"
     - "1807 Dupont Av S"
     - "1807 Dupont Avenue South"
     - "1807 Dupont av."

2. **Matching Structured Entries**
   - Filtered JSON outputs year-wise to identify matching records.

3. **Timeline Assembly**
   - Compiled all matching records in chronological order (1902–1950).
   - Displayed:
     - Full name
     - Spouse name (if any)
     - Occupation
     - Employer or Business Address

4. **Validation & Cross-Checking**
   - Compared structured data with:
     - Raw OCR text
     - Annotated page images
   - Manually corrected names, formatting issues, and partial matches.

---

## 🗺️ Visual Workflow

```text
Start
  ↓
Download Image Tiles (6 per page)
  ↓
Stitch to Full Image → OCR with EasyOCR
  ↓
Group Text Blocks by Line Height
  ↓
Gemini LLM for Text Correction
  ↓
Gemini LLM for Structured JSON Output
  ↓
Save (Text + Image + JSON)
  ↓
Normalize Address Variants
  ↓
Filter for "1807 Dupont Ave S" Entries
  ↓
Compile Timeline (1902–1950)
  ↓
Validate with Images & OCR Text
  ↓
Generate Final Report & LaTeX Output
You are a text-cleaning assistant. Fix spelling, punctuation, and spacing in this OCR paragraph from a 1904 directory...
Extract the following fields from this entry: First_Name, Last_Name, Spouse_Name (if any), Occupation, Employer_Business_Name_Address, Home_Address.
Output only valid JSON array.
## 🛠️ Tools Used

**Programming & OCR:**
- `Python`: Core scripting
- `requests`, `Pillow`, `OpenCV`, `EasyOCR`: Image processing and OCR

**AI & Language Models:**
- **Gemini LLM (Google Generative AI)**
  - `Gemini 1.5 Pro via API`: Structured data extraction

**Visualization:**
- `matplotlib`: Timeline plotting  
- `TikZ (LaTeX)`: Flowchart generation

**Documentation:**
- `LaTeX`: `report.tex`
- `Markdown`: `README.md`

---

## 📌 What You Can Do With This

- Recreate resident timelines for **any historical property**
- Extend the method to:
  - Other cities or states
  - Handwritten OCR (1800s and earlier)
- Apply in:
  - **Real estate storytelling**
  - **Family genealogy**
  - **Historical property research**

---

## 🖼️ Sample Files (Optional)

- `page_120.jpg`: Full scanned page from 1904 city directory
- `page_120_output.jpg`: Annotated image with OCR bounding boxes
- `page_120_structured.json`: Gemini-extracted structured data

---

## 📬 Final Question – Experience with Handwritten Records?

✅ **Yes.** Experience includes:
- Historical cursive datasets
- Tools: `Transkribus`, `Tesseract`
- Hybrid methods: Manual transcription + Gemini correction

This pipeline is easily extensible to **1800s handwritten documents** with minimal adjustments.

---

## 📎 License

**MIT License** – Free to use for researchers, educators, history platforms, and contributors.

---

## 🙌 Special Thanks

Big thanks to the **HouseNovel team** and Amanda for the opportunity to bring AI into public history with purpose and creativity.
