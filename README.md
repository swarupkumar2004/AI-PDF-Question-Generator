# AI-PDF-Question-Generator
# 📘 AI PDF Content Analysis and Question Generation

This project is a submission for an AI/Python Internship Assignment that focuses on processing educational PDFs to generate image-based multiple-choice questions (MCQs) using Python and AI.

---

## 📌 Assignment Overview

The goal is to create a Python-based tool that can:

1. Extract all **text and images** from a given educational PDF.
2. Use an AI model to generate **questions** from the extracted **visual information**.
3. Organize the extracted and generated content into a **structured JSON** file for further use.

---

## 📁 Files Included

| File | Description |
|------|-------------|
| `notebook.ipynb` | Google Colab notebook with all code for extraction, captioning, and question generation |
| `final_mcq_questions_with_answers.json` | Final structured dataset of image-based questions with options and correct answer index |
| `extracted_images/` | Folder containing extracted images from the PDF (can be partial for GitHub) |
| `requirements.txt` | Python dependencies used |
| `README.md` | This documentation file |

---

## 🛠️ Tools & Libraries Used

- **PyMuPDF (fitz)**: For image extraction from PDFs
- **pdfplumber**: For text extraction from PDFs
- **Pillow (PIL)**: For image handling
- **HuggingFace Transformers (BLIP)**: For image captioning
- **Python (3.10+)**

---

## 🧪 How It Works

### Step 1: PDF Content Extraction
- Text is extracted using `pdfplumber`.
- Images are extracted using `PyMuPDF` and saved as `pageX_imageY.png`.

### Step 2: Image Captioning
- Each extracted image is passed to BLIP (`Salesforce/blip-image-captioning-base`) to generate a caption.

### Step 3: Question Generation
- Captions are converted into exam-style questions.
- 3 random distractor image options + 1 correct image are included.
- Output includes the `correct_answer_index`.

### Step 4: JSON Output
Example structure:
```json
{
  "question": "Which image shows a cat with a blue collar?",
  "image": "extracted_images/page5_image3.png",
  "caption": "a cat with a blue collar and a white tail",
  "options": [
    "extracted_images/page5_image3.png",
    "extracted_images/page1_image3.png",
    "extracted_images/page6_image2.png",
    "extracted_images/page4_image5.png"
  ],
  "correct_answer_index": 0
}
````

---

## 📦 How to Run

1. Clone this repository or open `notebook.ipynb` in Google Colab.
2. Upload the sample PDF (e.g., *IMO class 1 Maths Olympiad Sample Paper*).
3. Run all cells to extract, caption, and generate questions.
4. View or download the output JSON.

---

## 📚 Dataset Source

Sample PDF used:
📄 *IMO Class 1 Maths Olympiad Sample Paper 2024-25*
(Provided via assignment link or manually uploaded)

---

## ✅ Output Summary

* Total questions generated: \~50+
* Format: MCQs with 4 options (images)
* JSON ready for integration into quiz systems or AI pipelines
