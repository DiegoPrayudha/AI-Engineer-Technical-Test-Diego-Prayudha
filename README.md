
# 🧠 AI Engineer Take-Home Test – Financial Document Extraction (EKAD)

This repository contains my solution for the **AI Engineer Take-Home Test**, focused on extracting and structuring financial data from the **annual financial statement of PT Ekadharma International Tbk (EKAD)**.  
The implementation uses **Python** with two main libraries: **pdfplumber** and **pandas**.

---

## ⚙️ Tools Used
- **pdfplumber** → used to open, crop, and extract text and numeric data from PDF pages.  
- **pandas** → used to structure, clean, and export extracted data into CSV or JSON format.

---

## 🧩 Task 1 – Data Extraction & Validation

### 🎯 Objectives
1. Obtain the EKAD annual financial statement (PDF format).  
2. Extract relevant financial figures such as items, section titles, and yearly numeric values (e.g., 2021 and 2020).  
3. Ensure the data is clean, complete, and structured.  
4. Save the results in a machine-readable format (CSV / JSON).

### ⚙️ Approach
- **PDF Parsing**  
  Each page is cropped to remove margins, then `pdfplumber` extracts word positions and font styles.  
- **Text Reconstruction**  
  Words are grouped by their Y-axis positions to form readable lines.  
- **Bold Detection**  
  Font names containing “Bold”, “Bd”, or “Black” are used to identify **sections** and **subsections**.  
- **Value Extraction**  
  Regular expressions locate and extract numeric values corresponding to the 2021 and 2020 columns.  
- **Validation**  
  Only lines with valid numeric pairs are appended to the result list.  
- **Output**  
  Results are stored in `output/extracted.csv` as a structured table.

---

## 🧾 Task 2 – Categorization & Structuring

### 🎯 Objectives
1. Identify summary lines that represent total values.  
2. Produce a clean, minimal JSON output containing only those totals and their respective figures.

### ⚙️ Approach
Since this solution focuses on rule-based processing without LLM categorization, **Task 2** is implemented as a **filtering step**:


- The **`item`** column contains the word **"total"** (case-insensitive).  
- The item name has **five words or fewer**, reducing noise from long text lines.  
- The final JSON contains only the columns **`item`**, **`2021`**, and **`2020`**.

---

## ✅ Summary

- **Task 1:** Extract structured numeric data from PDF using **pdfplumber** + **pandas**.  
- **Task 2:** Filter and structure items containing **“total”** into a concise JSON summary.  

This provides a clean foundation for future enhancement, such as category mapping or LLM-based interpretation in later iterations.
